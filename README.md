
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date,,>
-- Description:	<Description,,>
-- =============================================
ALTER PROCEDURE [dbo].[usp_RevertLotNo]
	-- Add the parameters for the stored procedure here
	@PLN_LOTNO NVARCHAR(20)
AS
BEGIN
SET IDENTITY_INSERT WTS_PLAN_DESC_REVERT ON
	INSERT INTO WTS_PLAN_DESC_REVERT(
			PLN_ID
		   ,[PLN_YEAR]
           ,[PLN_LOTNO]
           ,[PLN_LOT_NO_REF1]
           ,[PLN_LOT_NO_REF2]
           ,[PLN_LOT_NO_REF3]
           ,[PLN_LOT_NO_REF4]
           ,[PLN_LOT_NO_REF5]
           ,[PLN_LOT_NO_REF6]
           ,[PLN_LOTREF_ISSUE]
           ,[LI_LINE_CD]
           ,[LI_LINE_GROUP]
           ,[PLN_SETNDTO_LINE]
           ,[PST_CODE]
           ,[PLN_SEQ]
           ,[PLN_FLG]
           ,[PLN_PRD_PLAN_DATE]
           ,[PLN_TRIAL_1]
           ,[CS_CODE]
           ,[SZ_CODE]
           ,[CS_WireSize_Cond]
           ,[CS_WIRE_COND]
           ,[CS_WIRE_SIZE]
           ,[CS_Wire]
           ,[PLN_PRD_PATTERN]
           ,[PT_CODE]
           ,[PRD_WIRE]
           ,[PLN_STDARD_CODE]
           ,[PLN_PROD_CAPACITY]
           ,[PLN_PROD_RATIO]
           ,[CLR_CODE]
           ,[PP_CODE]
           ,[PLN_PREP_CODE]
           ,[PLN_PREP_TIME]
           ,[PLN_PROD_TIME]
           ,[PLN_PREP_TIME_CAL]
           ,[PLN_PROD_TIME_CAL]
           ,[PLN_LATER_BREAK_CAL]
           ,[PLN_LATER_BREAK_TIME_CAL]
           ,[PLN_BREAK_LATER]
           ,[PLN_PREP_START]
           ,[PLN_LINE_START]
           ,[PLN_LINE_STOP]
           ,[PLN_LINE_STOP_DATE]
           ,[PLN_LINE_START_DATE]
           ,[PLN_AFT_PREPARE]
           ,[PLN_AFT_PREP_TIME_CAL]
           ,[PLN_PLAN_STOP_CAL]
           ,[PLN_REMARK]
           ,[PLN_Verify]
           ,[PRD_QTY_CENTER]
           ,[PRD_QTY_6B]
           ,[PRD_QTY_12B]
           ,[PLN_MEAL_TIME]
           ,[PLN_DRUM_NO]
           ,[PLN_DRUM_MAX]
           ,[PT_CODE_TO]
           ,[PRD_OVER_PLN]
           ,[PLN_ORDERNO]
           ,[PLN_ORDER_LENGHT]
           ,[PLN_PACKING_TYPE]
           ,[PLN_ORDER_QTY]
           ,[PLN_AFT_PREPARE_SENDTO]
           ,[PLN_LOTSEQ]
           ,[PLN_HIGHVOL]
           ,[PLN_ADDUSER]
           ,[PLN_UPDUSER]
           ,[PLN_ADDTIME]
           ,[PLN_UPDTIME]
           ,[UDP_MACHINE]
           ,[LENGHT_MARK])
	SELECT * FROM WTS_PLAN_DESC
	WHERE PLN_LOTNO=@PLN_LOTNO

	--update import
	UPDATE WTS_PLAN_DESC_IMPORT
	SET PLN_LOTNO = 'REV-' + PLN_LOTNO
	WHERE PLN_LOTNO=@PLN_LOTNO


	DELETE FROM WTS_PLAN_DESC
	WHERE PLN_LOTNO=@PLN_LOTNO

SET IDENTITY_INSERT WTS_PLAN_DESC_REVERT OFF
END

[RPT ID] IN 
CALCULATETABLE(
        VALUES ( 'fact_RLS_RenalCare'[RPT ID] )
        , 'fact_RLS_RenalCare'[Email Address] = USERNAME()
)

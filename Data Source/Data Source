Data Sources = 
VAR _base =
    UNION(
        SUMMARIZE( 
            SELECTCOLUMNS( 'Fact_Sales', "Data Source", 'Fact_Sales'[Data Source] ),
            [Data Source]
        ),
        // Add another expression or table here for the union
        // For example, you can use the same pattern for another table
        SUMMARIZE( 
            SELECTCOLUMNS( 'AOP Fact Data', "Data Source", 'AOP Fact Data'[Data Source] ),
            [Data Source]
        )
    )
VAR _addCategories =
    ADDCOLUMNS(
        _base,
        "Input or Backend",
        SWITCH(
            TRUE(),
            CONTAINSSTRING([Data Source], "Input"), "Input",
            CONTAINSSTRING([Data Source], ".xlsx"), "Input",
            CONTAINSSTRING([Data Source], "Corporate S4 Reconciliation Input"), "Input",
            CONTAINSSTRING([Data Source], "Greater China S4 Revenue Adj"), "Input",
            CONTAINSSTRING([Data Source], "Americas S4 Revenue Adj"), "Input",
            CONTAINSSTRING([Data Source], "EMEA S4 Revenue Adj"), "Input",
            CONTAINSSTRING([Data Source], "SNOWFLAKE"), "Snowflake",
            "Input"
        ),
        "Data Source Category",
        SWITCH(
            TRUE(),
            CONTAINSSTRING( [Data Source], "P-Code Revenue" ), "CMR Revenue",
            CONTAINSSTRING( [Data Source], "SGM" ), "SGM",
            CONTAINSSTRING([Data Source], "GL_DTL"), "Weekly Sales",
            CONTAINSSTRING([Data Source], "PRFT_ANALYS"), "Weekly Sales",
            CONTAINSSTRING([Data Source], "Corporate S4 Reconciliation Input"), "Weekly Sales",
            CONTAINSSTRING([Data Source], "Greater China S4 Revenue Adj"), "Weekly Sales",
            CONTAINSSTRING([Data Source], "Americas S4 Revenue Adj"), "Weekly Sales",
            CONTAINSSTRING([Data Source], "EMEA S4 Revenue Adj"), "Weekly Sales",
            CONTAINSSTRING([Data Source], "Weekly Sales"), "Weekly Sales",
            CONTAINSSTRING([Data Source], ".xlsx"), "Input - Other",
            "Other"
        )
    )
VAR _addSourceFacts =
    ADDCOLUMNS(
        _addCategories,
        "Data Source Fact",
        SWITCH(
            TRUE(),
            CONTAINSSTRING([Data Source], "GL_DTL"), "Weekly Sales",
            [Data Source Category]
        )
    )
RETURN _addSourceFacts

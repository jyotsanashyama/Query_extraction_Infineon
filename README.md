# Query_extraction_Infineon

Used an approach where we are calculating similarities among both column names and data frame rows. The detailed explanation is as follows:

1. Load the dataset (no crucial pre-processing is needed as the input data provided is already in required format)
2. Create embeddings for all column names to capture their semantic relations with user queries
3. Create embeddigns for user query
4. Calculate similarities between these column and query embeddings
5. This will give us target columns in which the query needs to be searched by the LLM later during LLM inferencing.
6. Now create row descriptions for all rows: descriptions basically include all rows data for only target columns (refer to cell: )
7. Create embeddings for these row descriptions to find semantic relations with queries (the good part is, these embeddings only include target columns to be searched, hence improving LLM accuracy and speed)
8. Finally, calculate similarities with row embeddings and we have most relevant rows given that they had only relevant columns data in them
9. The row and column data will be provided to LLM now as context along with the query so it can directly give the exact required answer.

This is a robust, effective, fast, and scalable approach as it only targets top relevant rows and columns, hence decreasing input size significantly for LLM and imporving its efficiency and speed of the whole system.

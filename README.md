# League-Of-Legends-Data-Set




# NMAR Analysis
State whether you believe there is a column in your dataset that is NMAR. Explain your reasoning and any additional data you might want to obtain that could explain the missingness (thereby making it MAR). Make sure to explicitly use the term “NMAR.”

I believe the column firstbaron in my data set could be not missing at random (NMAR) because when I set the datacompleteness column to complete and check for all the null values, there are 320 rows where firstbaron is null. The firstbaron column does not rely on any other columns as it is own objective, it just relies on the column itself. I was also thinking that this column could possibly be NMAR because what if these games ended without firstbaron so that means that those games geniuenly don't have firstbaron. If I knew more information about of the data was collected then I might be able to make it MAR. For example, if there was complications in collecting data for the firstbaron and that is why those values are missing. Even if the datacompleteness column was queried to complete, there may have been issues in collecting this data. If I new this information then I would be able to determine it as MAR. There are 320/19430 rows that are missing the firstbaron data.  
# Case Study Tech

- You have 24 hours time (that being said we are not expecting to work 24 hours on the task,
  rather it would be great if you could reserve about 2 hours of your time to think about
  the problem and sketch out some ideas).
- Your answers can be in English or Portuguese, whatever you prefer.
- All non-human help is allowed. You can use the Internet and any site and tools
  you want. If you have questions about the tasks please don't hesitate to ask!
- Read the tasks carefully and solve them as described.
- Optionially download the datasets
[Training Dataset](https://drive.google.com/file/d/11IOZTBkOxXt9z7tE12B4Skz3oyw60MIV/view?usp=sharing)
[Test Dataset](https://drive.google.com/file/d/1rFsRexhruCxl6MFPAe3JVjwK-wTxRzAW/view?usp=sharing)
- After you finished, please send an email with your solution to: georg.buske@dafiti.com.br
  Use the following subject line: Case Study Tech R&D - <YOUR_NAME>

## Your tools

- Editor/IDE and the tools you choose :-)

## The project

Dafiti Sales Conversion Prediction



Given the provided training dataset (data_challenge_case_study_training.csv)
with data, create a solution to predict if a user (identified by fullVisitorId)
will buy (isTransaction = true) or not (isTransaction = false).
You can use any tool you want, also feel free to transform the data in the way
you think it makes most sense. There are no right or wrong answers but we want
to unerstand your approach. You can write an algorithm in pseudo-code, SQL,
Python, R or just plain-text, or whatever method you prefer - as long as we could
understand how you want to solve the problem it is all good. If you create a
working prototype (which of course would be a big plus) you can test your
assumption with the test datdaset data_challenge_case_study_test.csv (which contains
the placeholder PREDICTED_VALUE in the transaction column).
The datasets are available to download in gzipped csv format (`gzip -d FILE_NAME.csv.gz`).

Each row has the following attributes:

```
fullVisitorId: unique user id
visitId: session id
visitStartTime: The timestamp (expressed as POSIX time).
date: The date of the session in YYYYMMDD format.
channelGrouping: The Default Channel Group associated with an end user's session for this View. Possible values are: Direct, Display, Email, Organic Search, Paid Search, Referral, Social, (Other)
deviceCategory: The type of device (Mobile, Tablet, Desktop).
city: Users' city, derived from their IP addresses or Geographical IDs.
eCommerceActionType: Type of the action on the site. Possible values are: product-list, product-detail, add-product, remove-product, checkout, order-success, unknown.
isTransaction: true, if the made a successful transaction (order placed). This is the value which needs to be predicted in the test data set.
hitNumber: The sequenced hit number. For the first hit of each session, this is set to 1.
hour: The hour in which the hit occurred (0 to 23).
isEntrance: If this hit was the first pageview or screenview hit of a session, this is set to true.
isExit: If this hit was the last pageview or screenview hit of a session, this is set to true.
productSKU: the Product SKU.
isClick: Whether users clicked this product when it appeared in the product list.
productBrand: The brand associated with the product.
productPrice: The price of the product, expressed as the value passed to Analytics multiplied by 10^6 (e.g., 2.40 would be given as 2400000).
```

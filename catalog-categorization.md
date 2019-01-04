# Case Study Tech

- You have 24 hours time (that being said we are not expecting to work 24 hours on the task,
  rather it would be great if you could reserve about 2 hours of your time to think about
  the problem and sketch out some ideas).
- Your answers can be in English or Portuguese, whatever you prefer.
- All non-human help is allowed. You can use the Internet and any site and tools
  you want. If you have questions about the tasks please don't hesitate to ask!
- Read the tasks carefully and solve them as described.
- Optionally download the product dataset
  [here](https://s3.us-east-2.amazonaws.com/case-study.dafiti.gfg.science/catalog-data.csv.gz)
- After you finished, please send an email with your solution to: georg.buske@dafiti.com.br
  Use the following subject line: Case Study Tech R&D - <YOUR_NAME>

## Your tools

- Editor/IDE and the tools you choose :-)

## The project

Dafiti Product Catalog Categorization

### Your task

Dafiti's catalog is receiving lots of new products on a daily basis where
each product must have 1 or more categories, but more than often the associcated
categories for new products are simply wrong. We need to have a solution to
identify if the given categories are correct.

As mentioned above a dataset with ~300.000 products is as download available.
The product / category associations in the existing dataset (catalog-data.csv)
are considered correct. The file `categories.txt` has a list of all allowed
categories. The hierarchy is not important at this point in time. It must be
noted that ~16 % of the images associated with the products in the current
dataset / database are not available - this might be due to temporarily or
permanent errors. In general new products must have a valid image.

Choose whatever seems to be appropriate. Basically there are no technical
limitations.

A product has the following attributes:

```
    sku: this is the unique product identifier
    price: the price of the product
    name: the name of the product
    brand: the brand name of the product
    type: the product type, possible values are:
        accessories, apparel, babies, beauty, freesample, gifts, home, shoes, sportsacessories, sportsapparel, sportsequipment, sportsshoes, valepresente
    categories: categories associated to the product
        (The categories field in CSV file is comma separated, too. The file categories.txt has a list of all allowed categories.)
    product_image_url: the public url of the image
```

### Details

Following an example in JSON format:

```json
    {
        "sku": "BATMAN-123",
        "price": "122.99",
        "name": "Batmobile",
        "brand": "Marvel",
        "type": "accessories",
        "categories": ["Super Heroes", "Flying Cars", "Cars"],
        "product_image_url": "http://static.dafiti.com.br/9527534/1-zoom.jpg",
    }
```

To import the dataset and get you started you could use the following statements
in bash/MySQL (it might not be the best solution in terms of data storage, though):

```bash
gzip -d catalog-data.csv.gz;
sudo cp catalog-data.csv /var/lib/mysql-files
```

```sql
CREATE DATABASE IF NOT EXISTS catalog;
USE catalog;
DROP TABLE IF EXISTS product;
CREATE TABLE product (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    sku VARCHAR(50),
    price FLOAT(2),
    name VARCHAR(300),
    brand VARCHAR(100),
    type VARCHAR(50),
    categories VARCHAR(2047),
    product_image_url VARCHAR(255)
);
LOAD DATA INFILE '/var/lib/mysql-files/catalog-data.csv'
INTO TABLE product
FIELDS TERMINATED BY ';' OPTIONALLY ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 LINES
(sku, price, name, brand, type, categories, product_image_url)
SET id = NULL;
```

_That's it. Good luck!_


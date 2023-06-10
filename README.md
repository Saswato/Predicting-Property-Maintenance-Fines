# Predicting Property Maintenance Fines

Blight violations are issued by the city to individuals who allow their properties to remain in a deteriorated condition. The city of Detroit wants to increase blight ticket compliance by understanding the factors that contribute to non-compliance. In this project, we use predictive modeling to predict whether a given blight ticket will be paid on time.

## Data Description

The dataset consists of two files:

- `train.csv`: the training set containing information about blight tickets issued from 2004 to 2011.

Data fields in `train.csv` include:
- `ticket_id`: unique identifier for tickets
- `agency_name`: agency that issued the ticket
- `inspector_name`: name of the inspector who issued the ticket
- `violator_name`: name of the person/organization to whom the ticket was issued
- `violation_street_number`, `violation_street_name`, `violation_zip_code`: address where the violation occurred
- `mailing_address_str_number`, `mailing_address_str_name`, `city`, `state`, `zip_code`, `non_us_str_code`, `country`: mailing address of the violator
- `ticket_issued_date`: date and time the ticket was issued
- `hearing_date`: date and time of the violator's hearing
- `violation_code`, `violation_description`: type of violation
- `disposition`: judgment and judgment type
- `fine_amount`: violation fine amount, excluding fees
- `admin_fee`: $20 fee assigned to responsible judgments
- `state_fee`: $10 fee assigned to responsible judgments
- `late_fee`: 10% fee assigned to responsible judgments
- `discount_amount`: discount applied, if any
- `clean_up_cost`: DPW clean-up or graffiti removal cost
- `judgment_amount`: sum of all fines and fees
- `grafitti_status`: flag for graffiti violations
- `payment_amount`: amount paid, if any
- `payment_date`: date payment was made, if received
- `payment_status`: current payment status as of Feb 1, 2017
- `balance_due`: fines and fees still owed
- `collection_status`: flag for payments in collections
- `compliance`: target variable for prediction (Null = Not responsible, 0 = Responsible, non-compliant, 1 = Responsible, compliant)
- `compliance_detail`: more information on why each ticket was marked compliant or non-compliant

## Code Description

The provided code performs the following steps:

1. Reads the data from the `train.csv` file and removes records where the `compliance` field is null.
2. Adds a derived field called `hearing_days`, which represents the number of days between the hearing date and ticket issuance date.
3. Splits the data into training and testing sets with an 80:20 ratio.
4. Scales the numerical features using the min-max algorithm.
5. Adds dummy variables for categorical features.
6. Removes redundant features.
7. Uses the Sequential Feature Selection (SFS) method with a Random Forest Classifier to select the best features.
8. Prints the best score and the selected features.

## Dependencies

The code requires the following libraries:

- pandas
- numpy
- scikit-learn
- mlxtend

Please make sure these libraries are installed before running the code.

## Evaluation

The evaluation metric for this project is the Area Under the ROC Curve (AUC).

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).

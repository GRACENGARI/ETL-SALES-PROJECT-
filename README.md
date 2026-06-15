# Sales ETL Notebook

This workspace contains a single ETL notebook that reads sales data from CSV, transforms it with pandas, and loads the result into a MySQL table.

## Project Structure

- `Data/sales.csv`
- `Data/sales_2.csv`
- `src/etl.ipynb`
- `requirements.txt`

## What the Notebook Does

The notebook performs a simple ETL pipeline:

1. Extracts data from `Data/sales_2.csv`.
2. Cleans column names.
3. Converts `order_date` to datetime.
4. Converts `sales_amount` to numeric.
5. Creates a derived `unit_price` column.
6. Assigns a `sales_tier` label based on `sales_amount`.
7. Removes rows where `sales_amount` is not positive.
8. Adds a `load_timestamp` column.
9. Loads the transformed data into MySQL table `etl_transformed_sales`.

## Requirements

Install the Python packages listed in `requirements.txt`. The notebook uses:

- pandas
- numpy
- sqlalchemy
- pymysql

## Setup

1. Install dependencies.
2. Make sure MySQL is running.
3. Create the target database named `sales_db`.
4. Update the connection values in the notebook if needed.

## Configuration

The notebook uses these MySQL settings:

- User: `root`
- Password: `999111`
- Host: `localhost`
- Port: `3306`
- Database: `sales_db`
- Target table: `etl_transformed_sales`

If your environment is different, update those values before running the load step.

## Running the ETL

Open `src/etl.ipynb` and run the cells from top to bottom.

If you want to execute it outside the notebook, keep the same order of operations:

1. Load the CSV into a pandas DataFrame.
2. Clean and transform the data.
3. Create the SQLAlchemy engine.
4. Write the DataFrame to MySQL with `to_sql()`.

## Running in VS Code

1. Open the workspace in VS Code.
2. Open `src/etl.ipynb`.
3. Select the Python kernel that has the dependencies installed.
4. Run each cell in order.

If the notebook cannot find the CSV, update the path in the configuration cell so it matches your local workspace location.

## Notes

- The notebook currently reads from `D:/SANDBOX/Data/sales_2.csv`.
- If you move the workspace, update the CSV path in the notebook.
- The current `unit_price` logic copies `sales_amount` directly. If you want a real unit price calculation, that formula should be adjusted.

## Troubleshooting

- If `to_sql()` fails, verify that MySQL is running and that the `sales_db` database exists.
- If package imports fail, reinstall the dependencies from `requirements.txt` in the same Python environment used by the notebook.
- If the notebook shows a path error, make sure the drive letter and folder separators match your system.

## Output

Successful execution prints a confirmation message after loading the transformed data into MySQL.

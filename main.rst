.. code:: ipython3

    # initial imports
    import pandas as pd
    from pathlib import Path

.. code:: ipython3

    # set the file path
    csvpath = Path("../PyBank/budget_data.csv")

.. code:: ipython3

    # create a Pandas dataframe from a csv file
    budget_data = pd.read_csv(csvpath)

.. code:: ipython3

    # Read the CSV into a DataFrame using Pandas
    budget_data = pd.read_csv(csvpath)
    budget_data.head()




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>Date</th>
          <th>Profit/Losses</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>Jan-2010</td>
          <td>867884</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Feb-2010</td>
          <td>984655</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Mar-2010</td>
          <td>322013</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Apr-2010</td>
          <td>-69417</td>
        </tr>
        <tr>
          <th>4</th>
          <td>May-2010</td>
          <td>310503</td>
        </tr>
      </tbody>
    </table>
    </div>



.. code:: ipython3

    budget_data.describe()




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>Profit/Losses</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>count</th>
          <td>8.600000e+01</td>
        </tr>
        <tr>
          <th>mean</th>
          <td>4.463090e+05</td>
        </tr>
        <tr>
          <th>std</th>
          <td>5.363579e+05</td>
        </tr>
        <tr>
          <th>min</th>
          <td>-1.196225e+06</td>
        </tr>
        <tr>
          <th>25%</th>
          <td>1.821620e+05</td>
        </tr>
        <tr>
          <th>50%</th>
          <td>5.703280e+05</td>
        </tr>
        <tr>
          <th>75%</th>
          <td>7.952262e+05</td>
        </tr>
        <tr>
          <th>max</th>
          <td>1.170593e+06</td>
        </tr>
      </tbody>
    </table>
    </div>



.. code:: ipython3

    # Initialize variables, number_of_months, total_profit, average_change, greatest_increase, greates_decrease
    number_of_month = ()
    total_profit = ()
    monthly_change = ()
    average_change = () 
    greatest_increase = () 
    greates_decrease =()

.. code:: ipython3

    # count number of months
    index = budget_data.index
    number_of_month = len(index)
    print(f"Total Months {number_of_month}")


.. parsed-literal::

    Total Months 86
    

.. code:: ipython3

    # calculate the total profit
    total_profit = budget_data['Profit/Losses'].sum()
    print(f"Total profit:  ${total_profit}")


.. parsed-literal::

    Total profit:  $38382578
    

.. code:: ipython3

    # add column and calculate the changes
    
    budget_data['monthly_change'] = budget_data['Profit/Losses'].diff()
    budget_data
    

.. code:: ipython3

    # calculate average monthly change
    mo_ave = budget_data['monthly_change'].mean()
    
    rd_ave = round(mo_ave, 2)
    
    print(f"Average Change: ${rd_ave}")


.. parsed-literal::

    Average Change: $-2315.12
    

.. code:: ipython3

    # find the greatest increase in profit
    max_increase = budget_data[['Date', 'monthly_change']][budget_data['monthly_change']==budget_data['monthly_change'].max()]
    print("Greatest Increase in Profits")
    print(max_increase)


.. parsed-literal::

    Greatest Increase in Profits
            Date  monthly_change
    25  Feb-2012       1926159.0
    

.. code:: ipython3

    # find the greatest increase in profit
    max_decrease = budget_data[['Date', 'monthly_change']][budget_data['monthly_change']==budget_data['monthly_change'].min()]
    print("Greatest Decrease in Profits")
    print(max_decrease)


.. parsed-literal::

    Greatest Decrease in Profits
            Date  monthly_change
    44  Sep-2013      -2196167.0
    


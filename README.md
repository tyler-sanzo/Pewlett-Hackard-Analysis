# Pewlett-Hackard-Analysis

## Overview
Using SQL, we are providing a company with information on employees eligible for retirement. To prepare them for this wave of potential retirees, they would like a breakdown of employees by department and those who can assist in the mentorship program.

## Results

- To retrieve the list of employees eligible for retirement we had to perform a number of joins to ensure we had all required information
    - Inner join employees and titles.
    - Create a table from this join where birth dates were between 1952 and 55.
    - Use the distinct function to rid duplicates and order by to return the most recent titles.
    - Create another table from the above query using the count of employee ID's and merged on titles to get a table of eligible retirees by department.

| Count  | Title             |
| ---    |    ---            |
| 29414  | Senior Engineer   |
| 28254  | Senior Staff      |
| 14222  | Engineer          |
| 12243  | Staff             |
| 4502   | Technique Leader  |
| 1761   | Assistant Engineer|
| 2      | Manager           |

- Creating a table of retirees eligible for the mentorship program followed a similar process but the birth date range was confined to 1965.



## Analysis


### How many roles will need to be filled as the "silver tsunami" begins to make an impact?

Because we have already have a table created for the amount of potential retirees from each department, we can simply use the sum function on the count row from retiring_titles table.

```
SELECT SUM(count)
FROM retiring_titles;
```

Here we get a grand total of 90,308 employees.


### Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?

Using methods learned within this module, we can create a new table to display mentorship ready retirees by title and compare that number to the total number of employees eligible for retirement by title.

```
SELECT COUNT(title), title
INTO mentorship_by_titles
FROM mentorship_eligibility
GROUP BY title
ORDER BY COUNT(title) DESC;
```

Here we can see that the number of employees eligible for mentorship will not cover the total number of employees retiring by title. Pewlett-Hackard would be wise to outsource this work from a consulting firm if they want a smooth handoff to the fresh hires.

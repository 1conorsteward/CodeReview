# CodeReview
A code review for Appointment Now and Investment Calculator.

Appointment Now

Software Engineering/Design
❏ Does the code completely and correctly implement the design?
The design is correctly implemented for its intended functionalities, such as user registration, login, event management, and permission handling. It is implemented correctly based on the file names and class structures.
❏ Does the code conform to any pertinent coding standards?
The code generally follows Java coding conventions in that class names are in PascalCase, and method and variable names are in camelCase. However, some comments appear incomplete or missing. Improving comments will be helpful for maintenance, refactoring, or adding functionality to the code.
❏ Is the code well-structured, consistent in style, and consistently formatted?
The code is well-structured, with each activity handling specific functionalities. There is a clear separation of concerns within the modular code. In addition, formatting is consistent, with proper indentation and spacing.
❏ Are there any uncalled-for or unneeded procedures or any unreachable code?
There is no unreachable code or redundant procedures within this code.
❏ Are there any leftover stubs or test routines in the code?
There are no leftover stubs or tests within the code. It would be best practice to keep a production and a test Appointment Now within the repository, as it will help to put a new rendition of code into production if new tests do not need to be fully rewritten each time a new version comes out.
❏ Can any code be replaced by calls to external reusable components or library functions?
The code could benefit from reusing Android's built-in components or libraries where appropriate, as this will aid in adding complexity later. For example, more reusable utility classes or methods could reduce redundancy.
❏ Are there any blocks of repeated code that could be condensed into a single procedure?
There is not currently any repeated code but moving overly complex classes into separate utility cases should be considered as certain classes are needlessly complex.
❏ Are any modules excessively complex and should be restructured or split into multiple routines?
AddEventDialog fragment contains a saving functionality that could be split into a utility for the sake of reusability. EventDisplayActivity also contains several functionalities that could well be utilities as well including edit, delete, and save functions.
❏ Is the code clearly and adequately documented with an easy-to-maintain commenting style?
Comments vary from clear and adequate to missing entirely. This code would benefit greatly from added comments.
❏ Are all comments consistent with the code?
The comments, where they exist, are consistent with the purpose of the code but could be more detailed in some cases.
❏ Are all variables properly defined with meaningful, consistent, and clear names?
Variables follow standardization practices and naming conventions.
❏ Do all assigned variables have proper type consistency or casting?
Type consistency appears to be maintained.
❏ Are there any redundant or unused variables?
No obvious redundant or unused variables are present.
Algorithms
❏ Are symbolics used rather than “magic number” constants or string constants?
No magic numbers exist within this code. 
❏ Does the code avoid comparing floating-point numbers for equality?
Yes, there are no floating point numbers within this code.
❏ Does the code systematically prevent rounding errors?
While not specifically applicable to this code, rounding errors should be prevented.
❏ Does the code avoid additions and subtractions on numbers with greatly different magnitudes?
There are no such operations within this code.
❏ Are divisors tested for zero or noise?
While there are no division cases in this code, this should be tested if there are any later.
❏ Does every case statement have a default?
While there are no switch cases in this code, ensuring a default for any that come later is vital.
❏ Are loop termination conditions obvious and invariably achievable?
Termination conditions are obvious and achievable in this code.
❏ Are all loops, branches, and logic constructs complete, correct, and properly nested?
Yes, all loops, branches and logic constructs are complete, correct, and properly nested.
❏ Are the most common cases tested first in IF- -ELSEIF chains?
No, as there are no IF-ELSE loops in this code.
❏ Are all cases covered in an IF- -ELSEIF or CASE block, including ELSE or DEFAULT clauses?
Yes, but only because IF-ELSE blocks are not present in this code. A for loop is used as well as a while loop.
❏ Are indexes or subscripts properly initialized, just prior to the loop?
There are only 2 loops in this code. 1 has proper initialization, the for loop in AddEventDialogFragment, while the other loop does not need initialization as it iterates over a cursor object.
❏ Can any statements that are enclosed within loops be placed outside the loops?
No, there are no statements within these loops that could be placed outside of the loops.
❏ Does the code in the loop avoid manipulating the index variable or using it upon exit from the loop?
There is no manipulation of the index variable in either loop.
Database Structure/Design
❏ Is storage use efficient?
Overall yes, but there are some adjustments that can be made. Indexes can be added for holding emails and event dates. Dates are currently stored at text but could be in a specific date format. SQLite and cursor objects need to be closed to prevent data leakage.
❏ Are indexes, pointers, and subscripts tested against array, record, or file bounds?
Yes, the applicable pieces of code are tested against the bounds of indexes.
❏ Are imported data and input arguments tested for validity and completeness?
There are currently no tests for validity and completeness except that the re-enter password is checked against the password when creating a new account. Considering that this app should be HIPPA compliant if released, all inputs and exports will need to be validated and encrypted before the app is released to the public.
❏ Are all output variables assigned?
Yes all output variables are assigned.
❏ Are the correct data operated on in each statement?
Yes, the data within each operation is the data that should be manipulated within that operation.
❏ Is every memory allocation deallocated?
NO! This is actually a large issue in that none of the memory allocated is ever closed.
❏ Are timeouts or error traps used for external device accesses?
Neither the DB or the notification feature have error traps or timeouts.
❏ Are files checked for existence before attempting to access them?
There are no files to check for existence before accessing them.
❏ Are all files and devices left in the correct state upon program termination?
No, many of the files and devices are left in an active state after the app has been closed. Cursors and runtime permissions need to be closed.

Enhancement Plan

I would like to add functionality to the application Appointment Now that allows different logins to have different schedules presented for their specific practice. This would allow a variety of practices to use the application. In addition, I would like to add the ability to see patient historical data and export those in a few different formats. In addition, I will implement a few quality of life adjustments within this code including updated and comprehensive commenting, closed states when the application is closed, timeout/error traps for the DB and SMS feature, and input validation. These were brought to my attention within this code review. Adding encrypted security is a task I wish to complete on my own later, as the above changes will take up more than enough time.

To complete the varying practice login I will need to:

Create a new table Practices with fields: id, practice_name, address, contact_info.
Add a foreign key practice_id to the Users table to associate a user with a specific practice.
Modify the Events table to include a practice_id to link appointments to a specific practice.
Update the login screen to identify the user’s practice.
Modify the schedule display screen to filter appointments based on the user's practice.
Update the login mechanism to fetch the practice_id for the logged-in user.
Modify schedule-fetching logic to filter appointments based on practice_id.

To make historical data available I will need to:

Create a new table PatientHistory with fields: id, patient_id, visit_date, notes, diagnosis, treatment.
Link this table to the existing Patients table via patient_id.
Add a button on the patient detail screen labeled "View History."
Create a new screen that lists all historical data for the selected patient.
Add export buttons (PDF, CSV) on this screen.
Create a function to fetch historical data for a patient from the PatientHistory table.
Use libraries to handle the export functionality for different formats.

Code review updates:

Update states in a closed format.
Add timeout/error traps for external device needs.
Apply input validation to all available inputs.
Ensure code commenting is thorough.

DB Enhancements:

 For displaying skill in databases, I would like to enhance Appointment Now to include a more complex SQLite database that can hold a larger variety of information, send that information, and store the information in an accessible location in the application. This will display my skills in database functionality and UI design. I made this application in CS 360.

To enact these changes I will need to:

Expand the current SQLite database schema to include new tables and relationships that cover a wider variety of data, such as appointment attachments, notification history, and user roles.
Create views, triggers, and indices to optimize data retrieval and ensure data integrity.
Implement a data storage mechanism for saving attachments and documents, allowing users to view and download them within the app.
Design a user interface to manage these enhanced data types effectively, ensuring a user-friendly experience.

Database Structure Needs:
Patients Table: Enhanced to include additional information such as insurance details and medical history.
Appointments Table: Expanded to include fields for appointment type, follow-up date, and linked attachments.
Attachments Table: New table to store documents and images related to appointments or patient records.
Notifications Table: New table to keep track of notifications sent to users regarding appointments or updates.

For data storage and UI enhancements:

Allow users to upload and view documents or images associated with an appointment.
Store files securely within the app's private storage or an external directory.
Add sections for viewing attachments and appointment history.
Include insurance details and medical history fields.
Show a list of past notifications with options to filter by type.
















Investment Calculator

Software Engineering/Design
❏ Does the code completely and correctly implement the design?
Yes, the code correctly implements the design for an investment calculator that handles user input, calculates monthly and yearly balances with and without deposits, and displays the results. InvestmentCalculator, and InvestmentReport are well-defined, and their methods complete the needed functionalities.
❏ Does the code conform to any pertinent coding standards?
Camel case, Pascal Case, and header guards are all used properly within the code, conforming to C++ standards.
❏ Is the code well-structured, consistent in style, and consistently formatted?
The code is generally well-structured and follows a consistent style. It is indented properly, with clear separation between the header and implementation files via tag descriptions. The use of spacing and line breaks makes it readable as well.
❏ Are there any uncalled-for or unneeded procedures or any unreachable code?
All methods are called at least once and there is no unreachable code.
❏ Are there any leftover stubs or test routines in the code?
No, all methods are called and are used appropriately.
❏ Can any code be replaced by calls to external reusable components or library functions?
With the current functionality there are no places where code would need to be replaced by standardized libraries, and some libraries are already in use within the code.
❏ Are there any blocks of repeated code that could be condensed into a single procedure?
There is a repetition of code for calculating yearly balances with/without deposits in InvestmentReport::displayStaticReports. This could be refactored into a separate function to avoid redundancy and improve maintainability.
❏ Are any modules excessively complex and should be restructured or split into multiple routines?
No, the modules are not excessively complex. The code is simple and straightforward.
❏ Is the code clearly and adequately documented with an easy-to-maintain commenting style?
The code includes some header comments, but more detailed comments explaining the purpose and functionality of each function would improve clarity and maintainability as well as making additional functionality easier to add.
❏ Are all comments consistent with the code?
Yes, the comments provided are consistent with the code but there should be more robust commenting generally.
❏ Are all variables properly defined with meaningful, consistent, and clear names?
Yes, all variables are defined with meaningful names that convey their purpose.
❏ Do all assigned variables have proper type consistency or casting?
Yes, all assigned variables have proper type consistency.
❏ Are there any redundant or unused variables?
No, there are no redundant or unused variables.
Algorithms
❏ Are symbolics used rather than “magic number” constants or string constants?
The code uses some "magic numbers", like 12 for monthsInYear. It would be best to define these as symbolic constants.
❏ Does the code avoid comparing floating-point numbers for equality?
The code does not compare any floating-point numbers.
❏ Does the code systematically prevent rounding errors?
The code uses std::fixed and std::setprecision(2) to control the output precision, which helps prevent rounding errors in display.
❏ Does the code avoid additions and subtractions on numbers with greatly different magnitudes?
The code does not perform any operations on numbers with greatly differing magnitudes that could lead to precision issues.
❏ Are divisors tested for zero or noise?
The code does not perform any divisions where a divisor could be zero.
❏ Does every case statement have a default?
Not applicable.
❏ Are loop termination conditions obvious and invariably achievable?
Yes, loop termination conditions are clear and achievable.
❏ Are all loops, branches, and logic constructs complete, correct, and properly nested?
Yes, For loops in calculateInvestment and displayStaticReports are correctly structured and nested.
❏ Are the most common cases tested first in IF- -ELSEIF chains?
The code does not have any if-else chains as the logic is handled directly within loops.
❏ Are all cases covered in an IF- -ELSEIF or CASE block, including ELSE or DEFAULT clauses?
Not applicable, see above.
❏ Are indexes or subscripts properly initialized, just prior to the loop?
Yes, loop indexes are properly initialized, like int month = 1; in calculateInvestment().
❏ Can any statements that are enclosed within loops be placed outside the loops?
The loop statements are appropriately placed. Moving them outside would change the logic.
❏ Does the code in the loop avoid manipulating the index variable or using it upon exit from the loop?
Yes, the index variables are only used within their respective loops.
Database Structure/Design
❏ Is storage use efficient?
The use of primitive data types is appropriate for the application’s needs. There are no memory-intensive operations.
❏ Are indexes, pointers, and subscripts tested against array, record, or file bounds?
The code does not use arrays, pointers, or subscripts where bounds checking is needed.
❏ Are imported data and input arguments tested for validity and completeness?
The user input is read directly without validation. Validation checks would be valuable.
❏ Are all output variables assigned?
Yes, all output variables are properly assigned before they are used.
❏ Are the correct data operated on in each statement?
Yes, the correct data types are operated on in each statement.
❏ Is every memory allocation deallocated?
The code does not perform manual memory allocation. All memory is managed automatically.
❏ Are timeouts or error traps used for external device accesses?
Not applicable, as the code does not involve external device access.
❏ Are files checked for existence before attempting to access them?
Not applicable, as the code does not involve file handling.
❏ Are all files and devices left in the correct state upon program termination?
Not applicable, as the code does not involve handling files or devices.

Enhancements

For demonstrating my skills in data structures and algorithms I would like to enhance files in my GitHub that calculates the investment potentials of two types of investing strategies to demonstrate more investment strategies. This will demonstrate my understanding of applying complex algorithms and will allow people to see various investment opportunities outcomes. These strategies include a Dividend Reimbursement Plan(An investment where dividends are automatically reinvested into purchasing more shares. This can demonstrate the power of compounding over time and how it affects overall returns) and High-Risk, High-Reward vs Low-Risk, Low-Reward strategy(Compare the outcomes of a high-risk portfolio against a low-risk portfolio. This would illustrate the different risk profiles and potential returns.). This came from a class for data analytics that I took through Google Coursera.

For the Dividend Reinvestment Plan:

Create the input parameters.
Initial investment amount.
Annual dividend yield (percentage).
Stock price (initial).
Growth rate of the stock price.
Number of years.
For each year, calculate the number of additional shares purchased using the dividends earned.
Adjust the total number of shares and calculate the new value of the investment.
Repeat the process for the entire investment period.
Display year-wise data showing initial investment, dividends earned, shares purchased, total shares, and ending balance.

For HRHR v LRLR Strategy:

Set input parameters
Initial investment amount.
Annual return rates for high-risk and low-risk portfolios (expected return and standard deviation).
Number of years.
For each portfolio, simulate the annual return using a normal distribution with given expected return and standard deviation.
Calculate the investment's value at the end of each year for both portfolios.
Display a comparative graph of the two portfolios over the investment period.
Graphs showing the growth of each portfolio over time.
Summary statistics for returns, risk, and potential loss.

Code review enhancements:

Input validation checks will be implemented.
Define magic numbers in symbolic restraints.

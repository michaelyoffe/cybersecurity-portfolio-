Algorithm for file updates in Python
Project description
In this project, I developed a python-based algorithm to automate updating an IP address allow list used to control access to restricted content at my organization. The “allow_list.txt” identifies IP addresses permitted to access sensitive systems, while a separate “remove_list.txt” identifies IP addresses that should no longer have access. The algorithm reads the “allow_list.txt” file, checks it against the “remove_list.txt”, and removes any matching IP addresses to ensure access permissions remain up to date. This automated approach helps reduce manual errors, improves security, and supports access control requirements in an environment that handles sensitive patient data. 
Open the file that contains the allow list
To open the file that contains the allow list, I first assigned the file name “allow_list.txt” to a variable called import_file. Storing the file name in a variable makes it easier to reuse. 


  ![Opening File Screenshot](screenshots/image1.png)



I then used a with statement along with the open() function in read mode (“r”) to open the file. 


  



In this algorithm the with statement ensures that the file is properly managed and automatically closed after the program finishes working with it, while the file object is stored in the variable file to reuse in later steps. 
Read the file contents
I used the .read() method to convert the file into a string so I could then read the file contents.    




The open() function is used with the “r” argument to open the “allow_list.txt” file for reading. The with keyword is used to create a context manager, which ensures the file is properly closed after it is read. The .read() method is then called on the file object to read the entire contents of the file and convert it into a string. This string is stored in a variable named ip_addresses, which allows the data from the file to be accessed and used in later steps of the algorithm. 
Convert the string into a list
The ip_addresses variable is converted from a string into a list so individual IP addresses can be accessed and removed which is why I needed to use the .split() method.


  



Since strings are immutable in Python, the .split() method is used to convert the string data into a list of individual IP addresses. This allows the program to iterate through the lists and remove specific IP addresses during later steps of the algorithm. 


Iterate through the remove list
A for loop is used to iterate through the remove_list.


  



The for keyword creates an iterative statement, and element is used as the loop variable to represent each IP address in the list one at a time. As the loop runs, python temporarily stores each IP address from remove_list in the element variable, allowing the program to check or progress each address individually in later steps of the algorithm. 
Remove IP addresses that are on the remove list
The .remove() method can be used safely in this scenario because there are no duplicate IP addresses in the ip_addresses list, ensuring that each IP address is removed only once. 


  



A for loop is used to iterate through each element in the ip_addresses list. An if conditional statement checks whether the current element is also present in the remove_list. If the condition evaluates to true, the .remove() method is applied to the ip_addresses list to remove that IP address.
Update the file with the revised list of IP addresses 
As the final step in the algorithm, the allow list file is updated with the revised list of IP addresses. The join() method is used to convert the list back into a string format, allowing the updated data to be written to the text file.


  



The join() method is used to convert the ip_addresses list back into a single string so it can be written to a text file. The newline character (“ ”) is used as a separator to ensure each IP address appears on its own line in the file. 


  



Next, a with statement is used with the open() function in write mode (“w”) to overwrite the original file with the revised list of IP addresses. The write() method updates the file contents, and the with statement ensures the file is properly closed after writing is complete. 
Summary
In this algorithm, I wrote a Python program that updates an allow list by removing specific IP addresses. The file is opened and read as a string, then split into a list using the split() method so each IP address can be checked individually. The program compares this list against a separate removal list and uses the remove() method when a matching IP address is found. Once the updates are complete, the list is converted back into a string with the join() method. The revised content is then written back to the original file to reflect the changes.


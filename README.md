# Record_Domain_Name_service
# Explanation of Key Concepts
1. DNS Records: DNS records are entries in a DNS zone file that map domain names to IP addresses and other resources.
   A Record: Maps a domain name to an IPv4 address.
   MX Record: Specifies the mail servers for a domain.
2. dnspython Library: A powerful library for working with DNS in Python, allowing for querying and manipulating DNS records.

# step-by-step to understand how it fetches DNS records for a given website and stores them in a dictionary.
Code Explanation
1. Importing Required Library
   -> import dns.resolver
*This imports the dns.resolver module from the dnspython library, which is used for querying DNS records.*
2.  Dictionary to Store DNS Records
   -> dns_record = {}
*Initializes an empty dictionary dns_record to store the DNS records.*
3. User Input for Website
   -> website = input("Enter the name of the website: ")
*Prompts the user to input the name of the website for which DNS records are to be fetched and stores the input in the variable website.*
4. Fetching 'A' Record
    -> a_record = dns.resolver.resolve(website, 'A')
for ipval in a_record:
    dns_record['A_Record_IP'] = ipval.to_text()
*Uses dns.resolver.resolve() to fetch the 'A' record for the specified website. The 'A' record maps the domain name to its corresponding IPv4 address.*
*Iterates through the resolved 'A' records (a_record). For each IP value (ipval), it converts it to text using ipval.to_text() and stores it in the dns_record dictionary with the key 'A_Record_IP'.*
5. List to Store MX Records
   ->mx_record_list = []
*Initializes an empty list mx_record_list to store MX records temporarily.*
6. Fetching MX Records
   ->mx_record = dns.resolver.resolve(website, 'MX')
for server in mx_record:
    mx_record_list.append(server)
for i, element in enumerate(mx_record_list):
    dns_record['MX_Record', i+1] = element
*Uses dns.resolver.resolve() to fetch the MX records for the specified website. MX records specify the mail servers responsible for receiving email for the domain.*
*Iterates through the resolved MX records (mx_record). For each mail server (server), it appends it to the mx_record_list.*
*Then, iterates through the mx_record_list and adds each MX record to the dns_record dictionary with keys 'MX_Record', i+1, where i+1 ensures unique keys for each MX record.*
7.  Displaying the Records
->for key, value in dns_record.items():
    print(f"{key} = {value}")
*Iterates through the dns_record dictionary and prints each key-value pair to the screen.*




#Summary
1.Imports: dns.resolver from dnspython for querying DNS records. 
2.Input: Prompt the user to enter the website name.
3.DNS Records: Fetch 'A' (IP) and 'MX' (Mail Exchange) records.
4.Storage: Store fetched records in a dictionary for easy access.
5.Output: Print the DNS records in a readable format.
6.This script provides a basic example of how to fetch and display DNS records for a given website using Python.

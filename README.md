# Empty dictionary to store contacts
contacts = {}

while True:
    print('\nContact Book App:')
    print('1. Add Contact')
    print('2. View Contact')
    print('3. Update Contact')
    print('4. Delete Contact')
    print('5. Search Contact')
    print('6. Total Count of Contacts')
    print('7. Exit')

    # Get user choice
    choice = input("Enter your choice: ")

    if choice == "1":
        # Add Contact
        name = input("Enter the name: ").strip()
        if name in contacts:
            print(f"The name '{name}' already exists.")
        else:
            age = input("Enter age: ")
            mobile = input("Enter the mobile number: ")
            email = input("Enter the email address: ")
            address = input("Enter the address: ")
            contacts[name] = {"age": age, "mobile": mobile, "email": email, "address": address}
            print(f"The contact for '{name}' has been added successfully.")

    elif choice == "2":
        # View Contact
        name = input("Enter the contact name to view: ").strip()
        if name in contacts:
            contact = contacts[name]
            print(f"\nName: {name}")
            print(f"Age: {contact['age']}")
            print(f"Mobile: {contact['mobile']}")
            print(f"Email: {contact['email']}")
            print(f"Address: {contact['address']}")
        else:
            print("Contact not found.")

    elif choice == "3":
        # Update Contact
        name = input("Enter the contact name to update: ").strip()
        if name in contacts:
            print("Enter new details (leave blank to keep current value):")
            contact = contacts[name]
            age = input(f"Age [{contact['age']}]: ") or contact['age']
            mobile = input(f"Mobile [{contact['mobile']}]: ") or contact['mobile']
            email = input(f"Email [{contact['email']}]: ") or contact['email']
            address = input(f"Address [{contact['address']}]: ") or contact['address']
            contacts[name] = {"age": age, "mobile": mobile, "email": email, "address": address}
            print(f"The contact for '{name}' has been updated successfully.")
        else:
            print("Contact not found.")

    elif choice == "4":
        # Delete Contact
        name = input("Enter the contact name to delete: ").strip()
        if name in contacts:
            del contacts[name]
            print(f"The contact for '{name}' has been deleted successfully.")
        else:
            print("Contact not found.")

    elif choice == "5":
        # Search Contact
        search_name = input("Enter the contact name to search: ").strip()
        found = False
        for name, details in contacts.items():
            if search_name.lower() in name.lower():
                print(f"\nFound: {name}")
                print(f"Age: {details['age']}")
                print(f"Mobile: {details['mobile']}")
                print(f"Email: {details['email']}")
                print(f"Address: {details['address']}")
                found = True
        if not found:
            print("Contact not found.")

    elif choice == "6":
        # Total Count of Contacts
        print(f"Total number of contacts: {len(contacts)}")

    elif choice == "7":
        # Exit the app
        print("Exiting the Contact Book App. Goodbye!")
        break

    else:
        print("Invalid choice. Please try again.")

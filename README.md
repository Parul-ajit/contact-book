# contact-book
task 3 contact book
contacts = []

def add_contact():
    """Add a new contact."""
    name = input("Enter name: ")
    phone = input("Enter phone number: ")
    email = input("Enter email: ")
    address = input("Enter address: ")

    contact = {
        "name": name,
        "phone": phone,
        "email": email,
        "address": address
    }
    contacts.append(contact)
    print("Contact added successfully!\n")

def view_contacts():
    """View all contacts."""
    if contacts:
        print("\nContact List:")
        for index, contact in enumerate(contacts, 1):
            print(f"{index}. {contact['name']} - {contact['phone']}")
    else:
        print("No contacts available.\n")

def search_contact():
    """Search for a contact by name or phone number."""
    search_query = input("Enter name or phone number to search: ").lower()
    found_contacts = [contact for contact in contacts if search_query in contact['name'].lower() or search_query in contact['phone']]

    if found_contacts:
        for contact in found_contacts:
            print(f"\nName: {contact['name']}\nPhone: {contact['phone']}\nEmail: {contact['email']}\nAddress: {contact['address']}\n")
    else:
        print("Contact not found.\n")

def update_contact():
    """Update an existing contact."""
    name = input("Enter the name of the contact to update: ").lower()
    for contact in contacts:
        if contact['name'].lower() == name:
            print(f"Updating contact: {contact['name']}")
            contact['phone'] = input("Enter new phone number: ")
            contact['email'] = input("Enter new email: ")
            contact['address'] = input("Enter new address: ")
            print("Contact updated successfully!\n")
            return
    print("Contact not found.\n")

def delete_contact():
    """Delete a contact."""
    name = input("Enter the name of the contact to delete: ").lower()
    for contact in contacts:
        if contact['name'].lower() == name:
            contacts.remove(contact)
            print(f"Contact '{name}' deleted successfully!\n")
            return
    print("Contact not found.\n")

def menu():
    """User interface for the contact management system."""
    while True:
        print("\nContact Management Application")
        print("1. Add Contact")
        print("2. View Contact List")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")
        choice = input("Enter your choice (1-6): ")

        if choice == '1':
            add_contact()
        elif choice == '2':
            view_contacts()
        elif choice == '3':
            search_contact()
        elif choice == '4':
            update_contact()
        elif choice == '5':
            delete_contact()
        elif choice == '6':
            print("Exiting the application. Goodbye!")
            break
        else:
            print("Invalid choice! Please enter a number between 1 and 6.")

menu()

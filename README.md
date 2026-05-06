# Inventory-Management-1753
Inventory Management for OOP
Hybrid Inventory Manager
A console-based inventory manager with a C data layer (binary file I/O) and a C++ UI layer (classes, STL vector + sort).
File Structureinventory_project/
├── include/
│   ├── inventory.h          # C struct + function declarations
│   └── InventoryManager.h   # C++ class declaration
├── src/
│   ├── inventory.c          # C backend (fread/fwrite/fseek)
│   ├── InventoryManager.cpp # C++ wrapper + STL sort
│   └── main.cpp             # Menu / input validation
├── Makefile
├── CMakeLists.txt
└── README.md
make
./inventory_managerUsing CMakemkdir build && cd build
cmake ..
cmake --build .
./inventory_managerClean build artefactsmake
Using MakeClean build artefacts
make clean
Test Cases
Add 3 items, restart, list all – Added items with IDs 1, 2, 3. Exited. Re-ran the program. List all showed all 3 items — persistence confirmed.
Duplicate ID rejected – Tried adding a second item with ID 1. Program printed [FAIL] Could not add (duplicate ID or I/O error) and did not overwrite the existing record.
Update persists after restart – Updated item ID 2's name and price. Exited and restarted. View item 2 showed the new values.
Deleted item hidden from list and view – Deleted item ID 3. List all no longer showed it; View item 3 returned [FAIL] Item not found or deleted. Record remains in the binary file with is_deleted = 1.
Invalid input recovery – Entered -5 for ID, a blank name, and -1.0 for price. Each time the program displayed an error message and re-prompted without crashing.

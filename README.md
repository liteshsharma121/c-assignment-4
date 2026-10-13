#include <iostream>
using namespace std;


void addBalance(int balance)
{
    balance = balance + 50;
    cout << "Balance inside function: " << balance << endl;
}


void addBalancePointer(int *balance)
{
    *balance = *balance + 50;
}


void addBalanceReference(int &balance)
{
    balance = balance + 50;
}

int main()
{
    int balance = 100;
    int *ptr = &balance;
    int &ref = balance;

    cout << "===== POINTER AND REFERENCE =====" << endl;
    cout << "Original balance: " << balance << endl;
    cout << "Using pointer: " << *ptr << endl;
    cout << "Using reference: " << ref << endl;

    *ptr = 150;
    cout << "After pointer change: " << balance << endl;

    ref = 200;
    cout << "After reference change: " << balance << endl;

    cout << "\n===== FUNCTION CALLS =====" << endl;

    int b1 = 100;
    addBalance(b1);
    cout << "After call by value: " << b1 << endl;

    int b2 = 100;
    addBalancePointer(&b2);
    cout << "After call by pointer: " << b2 << endl;

    int b3 = 100;
    addBalanceReference(b3);
    cout << "After call by reference: " << b3 << endl;

    cout << "\n===== DYNAMIC MEMORY =====" << endl;

    int *amount = new int(299);
    cout << "Recharge amount: " << *amount << endl;

    delete amount;
    amount = nullptr;
    cout << "Single memory released." << endl;

    int n;
    cout << "\nEnter number of recharges: ";
    cin >> n;

    if (n <= 0)
    {
        cout << "Invalid number of recharges." << endl;
        return 0;
    }

    int *recharge = new int[n];
    int total = 0;

    cout << "Enter recharge amounts: ";
    for (int i = 0; i < n; i++)
    {
        cin >> recharge[i];
        total = total + recharge[i];
    }

    cout << "Recharge amounts: ";
    for (int i = 0; i < n; i++)
    {
        cout << recharge[i] << " ";
    }

    cout << "\nTotal recharge amount: " << total << endl;

    delete[] recharge;
    recharge = nullptr;

    cout << "Array memory released." << endl;

    return 0;
}

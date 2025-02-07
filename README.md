- 👋 Hi, I’m @Mostafaali17
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

#include <iostream>

#include <string>

using namespace std;



// Function to get baggage and hand luggage limits based on passenger type

void getLimits(int passengerType, int &maxBaggage, int &maxHand, double &baggageWeightLimit, double &handWeightLimit) {



     if (passengerType == 1) { // Economy

        maxBaggage = 1;

        baggageWeightLimit = 23.0;

        maxHand = 1;

        handWeightLimit = 8.0;

    } else if (passengerType == 2) { // Business

        maxBaggage = 1;

        baggageWeightLimit = 32.0;

        maxHand = 2;

        handWeightLimit = 8.0;

    } else if (passengerType == 3) { // Business Star Membership

        maxBaggage = 2;

        baggageWeightLimit = 32.0;

        maxHand = 2;

        handWeightLimit = 8.0;

    } else if (passengerType == 4) { // Economy Star Membership

        maxBaggage = 2;

        baggageWeightLimit = 23.0;

        maxHand = 1;

        handWeightLimit = 8.0;

    } else if (passengerType == 5) { // Business Normal Membership

        maxBaggage = 2;

        baggageWeightLimit = 32.0;

        maxHand = 1;

        handWeightLimit = 8.0;

    }

}



// Function to check dimensions of baggage with constraints

void checkBaggageDimensions(double &length, double &width, double &height, double maxAllowed) {

    // Validate dimensions only once for baggage

    cout << "Note: For baggage, the maximum allowed total dimensions (length + width + height) should be less than or equal to " << maxAllowed << " cm.\n";



    // Validate height

    do {

        cout << "Enter height (in cm): ";

        cin >> height;

        if (height < 25 || height > 75) {

            cout << "Invalid input! height can't be less than 25 cm and greater than 75 cm. Please enter again.\n";

        }

    } while (height < 25 || height > 75);



    // Validate width

    do {

        cout << "Enter Width (in cm): ";

        cin >> width;

        if (width < 15 || width > 50) {

            cout << "Invalid input! width can't be less than 15 cm and greater than  50 cm. Please enter again.\n";

        }

    } while (width < 15 || width > 50);



    // Validate length

    do {

        cout << "Enter length (in cm): ";

        cin >> length;

        if (length < 10 || length > 33) {

            cout << "Invalid input! length can't be less than 10 cm and greater than  33 cm. Please enter again.\n";

        }

    } while (length < 10 || length > 33);

}



// Function to check dimensions of hand luggage with updated constraints

void checkHandDimensions(double &length, double &width, double &height, int maxAllowed) {

    // Validate dimensions only once for hand luggage

    cout << "Note: For hand luggage, the maximum allowed total dimensions (length + width + height) should be less than or equal to " << maxAllowed << " cm.\n";

    // Validate height

    do {

        cout << "Enter height (in cm): ";

        cin >> height;

        if (height <= 12 || height > 40) {

            cout << "Invalid input! height must be greater than 12 cm and less than or equal 40 cm. Please enter again.\n";

        }

    } while (height <= 12 || height > 40);





    // Validate width

    do {

        cout << "Enter width (in cm): ";

        cin >> width;

        if (width <= 8 || width > 23) {

            cout << "Invalid input! width must be greater than 8 cm and less than or equal 23 cm. Please enter again.\n";

        }

    } while (width <= 8 || width > 23);



     // Validate length

    do {

        cout << "Enter Length (in cm): ";

        cin >> length;

        if (length <= 18 || length > 55) {



            cout << "Invalid input! Length must be greater than 18 cm and less than or equal 55 cm. Please enter again.\n";

        }

    } while (length <= 18 || length > 55);

}



int main() {

    int passengerType;



    //Input Passenger Type selection

         cout << "Select Passenger Type by entering the corresponding number:\n";

        cout << "1. Economy\n";

        cout << "2. Business\n";

        cout << "3. Business Star Membership\n";

        cout << "4. Economy Star Membership\n";

        cout << "5. Business Normal Membership\n";



    // Input Passenger Type with validation

    do {



        cout << "Enter your choice: ";

        cin >> passengerType;



        if (passengerType < 1 || passengerType > 5) {

            cout << "Invalid input! Please enter a number between 1 and 5.\n";

        }

    } while (passengerType < 1 || passengerType > 5);



    int maxBaggage, maxHand;

    double baggageWeightLimit, handWeightLimit;

    getLimits(passengerType, maxBaggage, maxHand, baggageWeightLimit, handWeightLimit);



    int pieces,hand;

    double length, width, height;

    double piecesWeight, handsWeight;

    double totalFine = 0;



    // Checked-in baggage

    do {

        cout << "\nEnter the number of checked-in bags: ";

        cin >> pieces;

        if (pieces < 0) cout << "Invalid input! Number of bags cannot be negative.\n";

    } while (pieces < 0);



    if (pieces > maxBaggage) {

        int extraBags = pieces - maxBaggage;

        totalFine += extraBags * 1000;

        cout << "You have " << extraBags << " extra bags. Fine is: " << extraBags * 1000 << " EGP\n";

    }



    for (int j = 1; j <= pieces; ++j) {

        cout << "\nEnter dimensions for baggage " << j << ":\n";

        checkBaggageDimensions(length, width, height, 158); // max limited allowed dimensions for baggage

        do {

            cout << "Enter weight of bag " << j << " (in kg): ";

            cin >> piecesWeight;

            if (piecesWeight <= 0) cout << "Invalid input! Weight must be greater than zero. Please enter again.\n";

        } while (piecesWeight <= 0);



        if (piecesWeight > baggageWeightLimit) {

            totalFine += (piecesWeight - baggageWeightLimit) * 50;

            cout << "Bag " << j << " exceeds weight limit. Fine is: " << (piecesWeight - baggageWeightLimit) * 50 << " EGP\n";

        }

    }



    // Hand luggage

    do {

        cout << "\nEnter the number of hand luggages: ";

        cin >> hand;

        if (hand < 0) cout << "Invalid input! Number of hand luggages cannot be negative.\n";

    } while (hand < 0);



    if (hand > maxHand) {

        int extraHands = hand - maxHand;

        totalFine += extraHands * 1000;

        cout << "You have " << extraHands << " extra hand luggages. Fine is: " << extraHands * 1000 << " EGP\n";

    }



    for (int j = 1; j <= hand; ++j) {

        cout << "\nEnter dimensions for hand luggage " << j << ":\n";

        checkHandDimensions(length, width, height, 118); // max limited allowed dimensions for hand luggage

        do {

            cout << "Enter weight of hand luggage " << j << " (in kg): ";

            cin >> handsWeight;

            if (handsWeight <= 0) cout << "Invalid input! Weight must be greater than zero. Please enter again.\n";

        } while (handsWeight <= 0);



        if (handsWeight > handWeightLimit) {

            totalFine += (handsWeight - handWeightLimit) * 50;

            cout << "Hand luggage " << j << " exceeds weight limit. Fine is: " << (handsWeight - handWeightLimit) * 50 << " EGP\n";

        }

    }



    // Display total fine

    cout << "\nTotal fine for extra bags,hand luggages and weight is: " << totalFine << " EGP\n";



    return 0;

}

#include<bits/stdc++.h>
using namespace std;

class ShopKeeper{
    private:
    map<string, vector<int>> mp;
    int initialPrice = 0, afterApplyoff = 0, maximumGST = 0, finalTotal = 0;
    string GSTProductName;
    public:
    void insertItemsInCart(string productName, int unitPrice, int GST, int qualtity) {
        auto _find = mp.find(productName);

        if(_find != mp.end()) {
            mp[productName][0] = unitPrice;
            mp[productName][1] = GST;
            mp[productName][2] = qualtity;
            cout << "Item value is Updated" << endl <<  endl;
        }
        else {
            mp[productName].push_back(unitPrice);
            mp[productName].push_back(GST);
            mp[productName].push_back(qualtity);
            cout << "Items is added in basket" << endl << endl;
        }
    }

    vector<string> CalculatePrice() {
        // map<string, vector<int>> result;
        vector<string> vect;
        for(auto i = mp.begin(); i != mp.end(); i++) {
            
            //total for find GST
            int totalAmount = (i->second[0] * i->second[2]);
            int GSTAmount = (totalAmount * (i->second[1] / 100)) / 100; //finding GST
            initialPrice = initialPrice + (i->second[0] * i->second[2]); //Calculating Total Initial Price
            
            if(i->second[0] > 500) {
                int discount = (GSTAmount - ((GSTAmount * 5) / 100)); // finding disocunt after applyting GST
                finalTotal = finalTotal + (totalAmount - discount);
                // result[i->first].push_back(initialPrice); //
                // result[i->first].push_back(initialPrice - discount);
            }
            else {
                finalTotal = finalTotal + GSTAmount;
                // result[i->first].push_back(initialPrice);
                // result[i->first].push_back(0);
            }

            if(i->second[1] > maximumGST) {
                maximumGST = i->second[1];
                GSTProductName = i->first;
            }
        }

        vect.push_back(to_string(initialPrice));
        vect.push_back(to_string(finalTotal));
        vect.push_back(GSTProductName);

        return vect;
    }
};

int main() {
    ShopKeeper sk;
    int n = 1, price = 100, GST = 15, quantity = 5;
    string ProductName = "raju";
    cout << "how many Items you want to add : ";
    cin >> n;

    while (n--) {
        cout << "Enter Product Name : ";
        cin >> ProductName;
        cout << endl << "Enter Unit Price : ";
        cin >> price;
        cout << endl << "Enter GST percentage : ";
        cin >> GST;
        cout << endl << "Enter Quantity of the Product : ";
        cin >> quantity;

        sk.insertItemsInCart(ProductName, price, GST, quantity);
    }

    vector<string> result = sk.CalculatePrice();
    cout << "Total price is : " << result[0] << endl;
    cout << "You have to pay : " << result[1] << endl;
    cout << "Maximum GST Product is : " << result[2];  
    return 0;
}

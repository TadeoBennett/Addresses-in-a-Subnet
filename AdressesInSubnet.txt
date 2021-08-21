//Program that helps with finding the IP addresses in a subnet

#include <iostream>
using namespace std;

void menu(){
	cout<<"1. IP ranges"<<endl;
	cout<<"2. Usable IPs"<<endl;
	cout<<"3. Enter details"<<endl;
	cout<<"4. Exit"<<endl;
}
int main(){
	int fsoctet, soctet, toctet, froctet1, froctet2, blocksize, subnets;
	int savefroctet1, savefroctet2;
	
	cout<<"Enter the first octet : "; cin>>fsoctet;
	cout<<"Enter the second octet : "; cin>>soctet;
	cout<<"Enter the third octet value: "; cin>>toctet;
	cout<<"Enter the fourth octet value(0): "; cin>>froctet1;
	cout<<"Enter the number of subnets: "; cin>>subnets;
	cout<<"Enter the blocksize: "; cin>>blocksize;
	
	savefroctet1 = froctet1;
	savefroctet2 = froctet2;	
	
	int choice;
	menu();
	cin>>choice;
	
	while(choice != 4){
		froctet2 = blocksize - 1;
		cout<<"\n***********************************"<<endl;
		switch(choice){
			case 1://IP ranges
				for (int i = 0; i<subnets; i++){
					cout<<i+1<<".) "<<fsoctet<<"."<<soctet<<"."<<toctet<<"."<<froctet1;
					cout<<" to ";
					cout<<fsoctet<<"."<<soctet<<"."<<toctet<<"."<<froctet2<<endl;
					froctet1 += blocksize;
					froctet2 += blocksize;
				}//end for
				break;
			case 2:	//Usable IPs							
				for (int i = 0; i<subnets; i++){
					cout<<i+1<<".) "<<fsoctet<<"."<<soctet<<"."<<toctet<<"."<<froctet1 + 1;
					cout<<" to ";
					cout<<fsoctet<<"."<<soctet<<"."<<toctet<<"."<<froctet2 -1 <<endl;
					froctet1 += blocksize;
					froctet2 += blocksize;
				}//end for
				break;
			case 3:
				do{
					cout<<"Enter the first octet : "; 
					cin>>fsoctet;
					if (fsoctet > 255){
						cout<<"Error. Exceeds 255"<<endl;
					}					
				}while(fsoctet > 255);
				cout<<"Enter the second octet : "; cin>>soctet;
				cout<<"Enter the third octet value: "; cin>>toctet;
				cout<<"Enter the fourth octet value(0): "; cin>>froctet1;
				cout<<"Enter the number of subnets: "; cin>>subnets;
				cout<<"Enter the blocksize: "; cin>>blocksize;
				froctet2 += (blocksize - 1);
				savefroctet1 = froctet1;
				savefroctet2 = froctet2;				
				break;		
			default:
				cout<<"-->>Invalid"<<endl;		
		}//end switch
		froctet1 = savefroctet1;
		froctet2 = savefroctet2;
		cout<<"\n***********************************"<<endl;
		menu();
		cin>>choice;
	}//end while

	cout<<"\n\nMade by Tadeo Bennett"<<endl;
	cout<<"contact: tadeos.bennett@gmail.com"<<endl;
return 0;
}

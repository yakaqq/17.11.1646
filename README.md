# 17.11.1646
#include <iostream>
#include <conio.h>
#include <string>

using namespace std;

namespace menyu{
	void header(){
		cout<<"========================"<<endl;
		cout<<"Cafe Murni"<<endl;
		cout<<"========================"<<endl;
		cout<<"1. Food"<<endl;
		cout<<"2. Coffee"<<endl;
		cout<<"3. Non Coffee"<<endl;
		cout<<"4. Exit"<<endl;
		cout<<"========================"<<endl;
	}
	void food(){
		cout<<"1. Nasi Goreng"<<endl;
		cout<<"2. Mie Rebus"<<endl;
		cout<<"3. Singkong Goreng"<<endl;
		cout<<"========================"<<endl;
	}
	void coffee(){
		cout<<"1. Espresso"<<endl;
		cout<<"2. Aeropress"<<endl;
		cout<<"3. Drip"<<endl;
		cout<<"========================"<<endl;
	}
	void noncoffee(){
		cout<<"1. Avocado Juice"<<endl;
		cout<<"2. Strawberry Juice"<<endl;
		cout<<"3. Milkshake"<<endl;
		cout<<"========================"<<endl;
	}
}

class Cafe{
public:
	void setNomor(int no){
		nomor=no;
	}
	void setNama(string nama){
		this->nama=nama;
	}
protected:
	int nomor;
	string nama;
};

class food: public Cafe{
public:
	int getTotal(int jumlah, int harga){
		total = (harga * jumlah);
		return total;
	}
protected:
	int total;
};

class coffee: public Cafe{
public:
	int getTotal(int jumlah, int harga, int es){
		total =  (harga * jumlah) + (1000 * es);
		return total;
	}
protected:
	int total;
};

class noncoffee: public Cafe{
public:
	int getTotal(int jumlah, int harga){
		total = (harga * jumlah);
		return total;
	}
protected:
	int total;
};

void mainmenu(food f, coffee c, noncoffee n){
	int menu, no, pil, jumlah, es, harga;
	string ice;
	string nama;
	do{
		menyu::header();
		cin>>menu;

		if (menu == 1){
			menyu::food();
			cout<<"Pilihan : ";
			cin>>pil;
			cout<<"Nama : ";
			cin>>nama;
			cout<<"Nomor Meja : ";
			cin>>no;
			cout<<"Jumlah : ";
			cin>>jumlah;

			if (pil == 1){
				harga = 13000;
			}else if (pil == 2){
				harga = 6000;
			}else if (pil == 3){
				harga = 3000;
			}

			cout<<"========================"<<endl;
			cout<<"Total Harga = "<<f.getTotal(jumlah, harga)<<endl;

		}else if (menu == 2){
			menyu::coffee();
			cout<<"Pilihan : ";
			cin>>pil;
			cout<<"Nama : ";
			cin>>nama;
			cout<<"Nomor Meja : ";
			cin>>no;
			cout<<"Es [y/n] : ";
			cin>>ice;
			cout<<"Jumlah : ";
			cin>>jumlah;

			if (pil == 1){
				harga = 20000;
			}else if (pil == 2){
				harga = 25000;
			}else if (pil == 3){
				harga = 35000;
			}

			if (ice == "y"){
				es = 1;
			}else{
				es = 0;
			}

			cout<<"========================"<<endl;
			cout<<"Total Harga = "<<c.getTotal(jumlah, harga, es)<<endl;

		}else if (menu == 3){
			menyu::noncoffee();
			cout<<"Pilihan : ";
			cin>>pil;
			cout<<"Nama : ";
			cin>>nama;
			cout<<"Nomor Meja : ";
			cin>>no;
			cout<<"Jumlah : ";
			cin>>jumlah;

			harga = 15000;

			cout<<"========================"<<endl;
			cout<<"Total Harga = "<<n.getTotal(jumlah, harga)<<endl;

		}
	}while(menu != 4);
}

int main(void){
	food f;
	coffee c;
	noncoffee n;

	mainmenu(f, c, n);
	return 0;
}

# DATA-STRUCTURE--ADT
newcomer

#include<iostream>
using namespace std;
#include<string>

const int maxsize = 20;
template<class Datatype>
class Seqlist {
private:
	Datatype list[maxsize];
	int length;
public:
	Seqlist() { length = 0; }
	Seqlist(Datatype list[], int length);
	int Length() { return length; }
	Datatype pos_find(int i);//输入位置返回值
	int val_find(Datatype i);//输入值(Datatype)返回位置(int)
	void insert(int i, Datatype x);
	void Data_delete(int i);
	void Printlist();
};

template<class Datatype>
Seqlist<Datatype>::Seqlist(Datatype a[], int n) {
	if (n > maxsize) throw "wrong parameter";
	for (int i = 0; i < n; i++) {
		list[i] = a[i];
	}
	length = n;
}

template<class Datatype>
Datatype Seqlist<Datatype>::pos_find(int i) {
	return list[i];
}

template<class Datatype>
int Seqlist<Datatype>::val_find(Datatype a) {
	for (int i = 0; i < length; i++)
	{
		if (list[i] == a)return(i);
	}
	return -1;
}

template<class Datatype>
void Seqlist<Datatype>::insert(int i, Datatype x) {
	if (length + 1 > maxsize)throw "wrong parameter";
	for (int j = length; j >= i; j--) {
		list[j] = list[j - 1];
	}
	list[i] = x;
	length++;
}

template<class Datatype>
void Seqlist<Datatype>::Data_delete(int i) {
	if (length == 0)throw"wrong parameter";
	for (int j = i; j < length - 1; j++)
	{
		list[j] = list[j + 1];
	}
	list[length - 1] = NULL;
	length--;
}

template<class Datatype>
void Seqlist<Datatype>::Printlist()
{
	for (int i = 0; i < length; i++)cout << list[i] << " ";
}


int main()
{
	int a[10] = { 1,2,3,4,5,6,7,8,9,0 };
	Seqlist <int>ll(a, 10);
	ll.Printlist();
	cout << endl;
	ll.Data_delete(5);
	cout << endl;
	ll.Printlist();
	return 0;
}

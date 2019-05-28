////3. В магазине 5 касс, в каждый момент времени к кассе стоит очередь некоторой длины.Каждые 
////30 минут измеряется средняя длина очереди в каждую кассу и для каждой кассы это значение(
////число вещественное) записывается в соответсвующий ей файл(всего 5 файлов), магазин работает
////8 часов в день.Рассматривается только один день.На момент запуска приложения все значения уже 
////находятся в файлах.Написать программу, которая по данным замеров определяет интервал времени,
////когда в магазине было наибольшее количество посетителей за день.
#include <algorithm>
#include <vector>
#include <string>
#include <fstream>
#include <numeric>
#include <iostream>
using namespace std;
int main()
{
	setlocale(LC_ALL, "rus");
	 

	ifstream fin5;
	fin5.open("First.txt");

	vector< vector<int> > vc;
	vector<int> v5;
	while (!fin5.eof())
	{
		string str5 = " ";
		fin5 >> str5;
		int row5 = atoi(str5.c_str());
		getline(fin5, str5);
		v5.push_back(row5);
	}

	vc.push_back(v5);
	fin5.close();
	
	ifstream fin;
	fin.open("Second.txt"); 
	
	
	vector<int> v1;
		while (!fin.eof())
		{			
			string str = " ";
			fin >> str;
			int row = atoi(str.c_str());
			getline(fin, str);
			v1.push_back(row);
		}
		
		vc.push_back(v1);
		fin.close();
		 
		ifstream fin1;
		fin1.open("Third.txt");
		vector<int> v2;
		while (!fin1.eof())
		{
			string str1 = " ";
			fin1 >> str1;
			int row1 = atoi(str1.c_str());
			getline(fin1, str1);
			v2.push_back(row1);
		}
		vc.push_back(v2);
		fin1.close();

	ifstream fin2;
	fin2.open("Fourth.txt");
	vector<int> v3;
	while (!fin2.eof())
	{
		string str2 = " ";
		fin2 >> str2;
		int row2 = atoi(str2.c_str());
		getline(fin2, str2);
		v3.push_back(row2);
	}
	vc.push_back(v3);
	fin1.close();
		
	ifstream fin3;
	fin3.open("Fifth.txt");
	vector<int> v4;
	while (!fin3.eof())
	{
		string str3 = " ";
		fin3 >> str3;
		int row3 = atoi(str3.c_str());
		getline(fin3, str3);
		v4.push_back(row3);
	}
	vc.push_back(v4);
	fin3.close();

		
	vector <int> sum;
	for (int i = 0; i < 16; i++)
	{
		sum.push_back(vc[0][i]+ vc[1][i]+ vc[2][i]+ vc[3][i]+ vc[4][i]);
	}
	
	auto result = max_element(sum.begin(), sum.end());
	for (int i = 0; i < 16; i++)
	{
		if (sum[i] == *result)
		{
			if (i >= 14)
				cout << "На 17:";
			else if (i >= 12)
				cout << "На 16:";
			else if (i >= 10)
				cout << "На 15:";
			else if (i >= 8)
				cout << "На 14:";
			else if (i >= 6)
				cout << "На 13:";
			else if (i >= 4)
				cout << "На 12:";
			else if (i >= 2)
				cout << "На 11:";
			else if (i >= 0)
				cout << "На 10:";
			
			switch (i%2==0)
			{
			case true:
				cout<<"00 ";
				break;
			case false:
				cout << "30 ";
				break;			
			default:
				break;
			}
			cout << " пришлось максимальное посещение покупателей, в количестве: " << *result<<" человека";
		}	
	}
	 
	
	return 0;
}

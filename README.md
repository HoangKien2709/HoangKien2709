// Bai 5-Lab 3- Hoang Pho Kien
#include<iostream.h>
#include<math.h>
#include<iomanip>
#include<conio.h>
using namespace std;
int UCLN(int ts, int ms)
{
	for(int i=ts; i>0; i--)
	{
		if(ts%i==0 && ms%i==0)
			return i;
	}
}
class PS
{
		int ts, ms;
	public:
		PS(int ts=0, int ms=0)
		{
			this->ts=ts;
			this->ms=ms;
		}
		~PS(){}
		friend istream &operator >>(istream &is, PS &ps)
		{
			cout<<"Nhap tu so: ";
			is>>ps.ts;
			cout<<"Nhap mau so";
			is>>ps.ms;
			return is;
		}
		friend ostream &operator <<(ostream &os, PS ps)
		{
			os<<ps.ts<<"/"<<ps.ms<<endl;
			return os;
		}
		PS toi_gian()
		{
			PS temp;
			temp.ms = ms/UCLN(ms, ts);
			temp.ts= ts/UCLN(ms, ts);
			return temp;
		}
		PS operator+(PS &ps)
		{
			PS temp;
			temp.ts= ps.ts*this->ms+ ps.ms*this->ts;
			temp.ms= ps.ms*this->ms;
			return temp.toi_gian();
		}
		PS operator-(PS &ps)
		{
			PS temp;
			temp.ts= ps.ts*this->ms- ps.ms*this->ts;
			temp.ms= ps.ms*this->ms;
			return temp.toi_gian();
		}
		PS operator*(PS &ps)
		{
			PS temp;
			temp.ts= ps.ts*this->ts;
			temp.ms= ps.ms*this->ms;
			return temp.toi_gian();
		}
		PS operator/(PS &ps)
		{
			PS temp;
			temp.ts= ps.ts*this->ms;
			temp.ms= ps.ms*this->ms;
			return temp.toi_gian();
		}
};
 int main()
 {
 	PS ps, ps1, ps2;
 	cin>>ps1;
 	cin>>ps2;
 	ps= ps1+ps2;
 	cout<<"Tong: "<<ps<<endl;
 	ps= ps1-ps2;
 	cout<<"Hieu: "<<ps<<endl;
 	ps= ps1*ps2;
 	cout<<"Tich: "<<ps<<endl;
 	ps= ps1/ps2;
 	cout<<"Thuong: "<<ps<<endl;
 	return 0;
 }

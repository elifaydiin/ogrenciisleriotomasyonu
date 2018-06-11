# ogrenciisleriotomasyonu
#include <iostream> 

#include <conio.h> //getch(); fonksiyonu 

#include <fstream> // dosyalama  

#include <string> // string 

#include <clocale> // Türkçe karakter için

#include <iomanip> //setw() için 

#include <stdio.h>

using namespace std;

int main()

{

	string ogrAdi;	
	string ogrSoyadi;	
	int ogrNo;	
	int ogrSinif; 
	string bolum;
	string dersAdi; 
	string dersBolum; //ders modulu icin degiskenler

	int modul;//proje modulleri

	int secim;	
	int tercih;	
	int cevap;	
	string ogretimelemaniAdi;	
	string ogretimelemaniSoyadi;	
	string ogretimelemaniBolum;
	int sicilNo;//ogretim elemanlari icin degiskenler
	int ogrNot;//ogrenci notu 

	FILE *fp;	

	moduller://ilk acilan ana sayfa

	cout<<"MODUL SECINIZ"<<endl<<endl;

	cout<<"1- OGRENCI MODULU "<<endl;

	cout<<"2- OGRETIM ELEMANI MODULU "<<endl;

	cout<<"3- DERS MODULU "<<endl;

	cout<<"4- NOT MODULU "<<endl;

	cout<<"5- CIKIS "<<endl<<endl;

	cout<<"Modul Seciniz : ";cin>>modul;

	system("cls");

	switch(modul)

	{

		case 1://OGRENCI MODULU 

		{

			ogrenci:

			cout<<"OGRENCI MODULU "<<endl<<endl;
			cout<<"1- OGRENCI KAYIT"<<endl;
			cout<<"2- OGRENCI ARAMA"<<endl;
			cout<<"3- OGRENCI LISTELEME"<<endl;
			cout<<"4- OGRENCI BILGILERI DUZENLEME"<<endl;
			cout<<"5- MENUYE DON "<<endl;
			cout<<"  LUTFEN ISLEM SECİNİZ: ";cin>>secim;
			system("cls");
			switch(secim)

			{

				case 1://ogrenci kayit ekleme 

				{

					ekle1:

					cout<<" --OGRENCI KAYIT-- "<<endl;
					ofstream ogrenciEkle;
					ogrenciEkle.open("ogrenci.txt",ios::out | ios::in | ios::app);//dosyaya yazma islemi için 
					cout<<"Ogrenci Numarasi :";cin>>ogrNo;
					cout<<"Ogrenci Adi      :";cin>>ogrAdi;
					cout<<"Ogrenci Soyadi   :";cin>>ogrSoyadi;
					cout<<"Ogrenci Sinifi   :";cin>>ogrSinif;
					cout<<"Ogrenci Bolumu   :";cin>>bolum;
					ogrenciEkle<<ogrNo<<" "<<ogrAdi<<" "<<ogrSoyadi<<" "<<ogrSinif<<" "<<bolum<<endl<<endl;//dosyaya yazma islemi
					cout<<endl;
					ogrenciEkle.close(); //dosya kapatma
					cout<<"Yeni ogrenci Kaydi basarili bir sekilde yapilmistir."<<endl<<"Ust menuye donmek icin lutfen 1 e basiniz...";
					getch();
					system("cls");
					goto ogrenci;

					break;

				}

				case 2://ogrenci ARAMA

				{
					cout<<"OGRENCI ARAMA"<<endl;
					cout<<"1- Ogrenci Adina Gore Arama"<<endl;
					cout<<"2- Ogrenci No'ya Gore Arama"<<endl;
					cout<<"3- Bir ust menuye gidin "<<endl;
					cout<<" Secim yapiniz:";cin>>secim;
					system("cls");
					switch(secim)

					{

						case 1://ogrenci adina gore arama

						{

							cout<<"OGRENCI ADINA GORE ARAMA "<<endl<<endl;
							string arananAd;
							ifstream ogrAraAd;//dosyadan okuma islemi ve dosyayi acma 
							ogrAraAd.open("ogrenci.txt",ios::in);
							cout<<"Ogrenci Adi Giriniz:"; cin>>arananAd;
							cout<<endl;

							do 

					        { 	ogrAraAd>>ogrNo>>ogrAdi>>ogrSoyadi>>ogrSinif>>bolum; //dosya icindeki degiskenlerin okunmasi

					            if (arananAd == ogrAdi) //eger girilen deger ile dosya içindeki degerler ayni ise ogrenci bilgileri yazdiriliyor

								{ 

								cout<<"-- OGRENCI BILGILERI --"<<endl;
								cout<<"Ogrenci No    :"<<ogrNo<<endl;
								cout<<"Ogrenci Adi   :"<<ogrAdi<<endl;
								cout<<"Ogrenci Soyadi:"<<ogrSoyadi<<endl;
								cout<<"Ogrenci Sinif :"<<ogrSinif<<endl;
								cout<<"Ogrenci Bolumu:"<<bolum<<endl<<endl;  
								

								} 
								

					        } while (!ogrAraAd.eof()); 

					        ogrAraAd.close();
							cout<<"Ust menuye donmek icin lutfen 1 e basiniz...";
							getch();
							system("cls");

							goto ogrenci;

							break;

						}

						case 2://ogrenci no gore arama 

						{

							cout<<"OGRENCI NO GORE ARAMA "<<endl;
							ifstream ogrAraNo;//dosya okuma ve dosyayi acma 
							ogrAraNo.open("ogrenci.txt",ios::in);
							int arananNo;
							cout<<"Ogrenci No Giriniz:";
							cin>>arananNo;

							cout<<endl;

							do 

					        { 	

								ogrAraNo>>ogrNo>>ogrAdi>>ogrSoyadi>>ogrSinif>>bolum; //dosya icindeki degiskenlerin okunmasi

					            if (arananNo == ogrNo) 

								{ 

								cout<<" OGRENCI BILGILERI "<<endl;
								cout<<"Ogrenci No    :"<<ogrNo<<endl;
								cout<<"Ogrenci Adi   :"<<ogrAdi<<endl;
								cout<<"Ogrenci Soyadi:"<<ogrSoyadi<<endl;
								cout<<"Ogrenci Sinif :"<<ogrSinif<<endl;
								cout<<"Ogrenci Bolumu:"<<bolum<<endl;  

								} 

					        } while (!ogrAraNo.eof()); 

					        ogrAraNo.close(); //dosya kapatma
							cout<<"Ust menuye donmek icin lutfen 1 e basiniz...";
							getch();
							system("cls");

							goto ogrenci;

							break;

						}

						case 3:

						{

							goto ogrenci;//ust menuye donme 

						}	

						default:// farkli bir rakam gorulunce verilen uyari

						cout<<"Lutfen 1 le 3 arasinda bir rakam giriniz:";

						break;

					}

					

				}

				case 3://OGRENCi LiSTELEME

				{

					listele:

					cout<<"--OGRENCI LISTELEME--"<<endl;
					cout<<"1- Ogrenci Sinifina Gore Listeleme"<<endl;
					cout<<"2- Ogrenci Bolumune Gore Listeleme"<<endl;
					cout<<"3- Bir ust menuye gidin "<<endl;
					cout<<" Secim yapiniz:";cin>>secim;

					system("cls");

					switch(secim)

					{

						case 1://SINIFA GORE LISTELEME 

						{

							cout<<"OGRENCI SINIFINA GORE LISTELEME "<<endl;
							ifstream SinifListele;
							SinifListele.open("ogrenci.txt",ios::in); //dosya okuma ve dosyayy acma
							int girilensinif; 
							cout << "Aranilan Sinif :" ; 
							cin >> girilensinif;

					        do 

					        { 

					            SinifListele >> ogrNo >> ogrAdi >> ogrSoyadi >> ogrSinif >> bolum; //degiskenlerin okunmasi

					            if (ogrSinif == girilensinif) 

								{ 

								cout<<" --OGRENCI BILGILERI-- "<<endl;
								cout<<"Ogrenci No    :"<<ogrNo<<endl;
								cout<<"Ogrenci Adi   :"<<ogrAdi<<endl;
								cout<<"Ogrenci Soyadi:"<<ogrSoyadi<<endl;
								cout<<"Ogrenci Sinif :"<<ogrSinif<<endl;
								cout<<"Ogrenci Bolumu:"<<bolum<<endl<<endl;  

								} 

					        } while (!SinifListele.eof()); //dosya bitene kadar okunur

					        SinifListele.close(); //dosya kapatma

							cout<<"menuye donmek icin lutfen 1 e basiniz...";
							getch();
							system("cls");

							goto listele;

							break;

						}

						case 2://OGRENCI BOLUME GORE LISTELEME 

						{

							cout<<"OGRENCI BOLUMUNE GORE LISTELEME "<<endl;

							ifstream bolumListele;
							bolumListele.open("ogrenci.txt",ios::in); 
							string girilenBolum; 
							cout << "Aranilan Bolum :"; 
							cin >> girilenBolum;

					        do 

					        { 

					            bolumListele>>ogrNo>>ogrAdi>>ogrSoyadi>>ogrSinif>>bolum; 

					            if (bolum == girilenBolum) 

								{ //girilen bolum ile dosya icerisindeki bolumlerden ayni olanlari yazdiriyor

								cout<<"-- OGRENCI BILGILERI --"<<endl;
								cout<<"Ogrenci No    :"<<ogrNo<<endl;
								cout<<"Ogrenci Adi   :"<<ogrAdi<<endl;
								cout<<"Ogrenci Soyadi:"<<ogrSoyadi<<endl;
								cout<<"Ogrenci Sinif :"<<ogrSinif<<endl;
								cout<<"Ogrenci Bolumu:"<<bolum<<endl<<endl;  

								} 

					        } while (!bolumListele.eof()); 

					        bolumListele.close(); 

							cout<<"menuye donmek icin lutfen 1 e basiniz...";
							getch();
							system("cls");

							goto listele;

							break;

						}

						case 3:

						{

							goto ogrenci;

						}

						default:

						cout<<"Lutfen 1 le 3 arasinda bir rakam giriniz:";

						break;	

					}	

				}

				case 4://ogrenci bilgilerini GUNCELLEME

				{

					ifstream oku;//okuma yapmak icin 
					ofstream yaz;//yazma yapmak icin 

					int OgrenciDuzenle;

					cout<<"Guncelleme yapilacak ogrenci no :"; 	cin>>OgrenciDuzenle;
					oku.open("ogrenci.txt",ios::in);//okunacak dosya aciliyor
					yaz.open("guncellenmis_ogrenci.txt",ios::app);//yazilacak dosya aciliyor

					while(!oku.eof())//dosya sonuna kadar okuma

					{

						oku>>ogrNo>>ogrAdi>>ogrSoyadi>>ogrSinif>>bolum; 

						//dosya icerisindeki degerler okunuyor

					   if(ogrNo == OgrenciDuzenle)

					   {

					   	  	cout<<"Bilgilerinizi Guncelleyin"<<endl;//yeni bilgileri alir
							cout<<"Ogrenci No   : "; cin>>ogrNo;
							cout<<"Ogrenci Adi  : "; cin>>ogrAdi;
							cout<<"Ogrenci Soyad: "; cin>>ogrSoyadi;
							cout<<"Ogrenci Sinif: "; cin>>ogrSinif;
							cout<<"Ogrencinin Bolumu: ";cin>>bolum;

					   }

						yaz<<ogrNo<<" "<<ogrAdi<<" "<<ogrSoyadi<<" "<<ogrSinif<<" "<<bolum<<endl;

						

					}

					oku.close();
					yaz.close();

					remove("ogrenci.txt");//bu dosya siliniyor

					rename("guncellenmis_ogrenci.txt","ogrenci.txt");//guncellenmis adli dosyanin adi ogrenci olarak kayit ediliyor

					cout<<"Ogrenci bilgileri basarili bir sekilde guncellenmistir."<<endl<<"menuye donmek icin lutfen 1 e basiniz...";				 

					getch();
					system("cls");

					goto ogrenci;

					break;

				}

				case 5://ana manuye donme

				{

					goto moduller;	

				}

				default:

					cout<<"Lutfen 1 le 5 arasinda bir rakam giriniz"<<endl;

					break;			

			}

		}

		case 2://OGRETIM ELEMANI MODULU 

		{

			ogretimelemani:

			cout<<" OGRETIM ELEMANI MODULU "<<endl<<endl;
			cout<<"1- OGRETIM ELEMANI KAYIT"<<endl;
			cout<<"2- OGRETIM ELEMANI ARAMA"<<endl;
			cout<<"3- OGRETIM ELEMANLARINI LiSTELEME"<<endl;
			cout<<"4- OGRETIM ELEMANI BILGILERINI GUNCELLEME"<<endl;
			cout<<"5- MENUYE DON "<<endl;

			cout<<" LUTFEN BİR ISLEM SECINIZ: ";cin>>secim;

			system("cls");

			switch(secim)

			{

				case 1://ogretim elemani kayit

				{

					cout<<" OGRETIM ELEMANI KAYIT "<<endl;
					ofstream ogretimelemaniEkle; //dosyaya yazmak icin 
					ogretimelemaniEkle.open("ogretimelemani.txt",ios::app);
					cout<<"Ogretim Elemani Sicil No :";cin>>sicilNo;
					cout<<"Ogretim Elemani Adi      :";cin>>ogretimelemaniAdi;
					cout<<"Ogretim Elemani Soyadi   :";cin>>ogretimelemaniSoyadi;
					cout<<"Ogretim Elemani Bolumu   :";cin>>ogretimelemaniBolum;
					ogretimelemaniEkle<<"  "<<sicilNo<<" "<<ogretimelemaniAdi<<" "<<ogretimelemaniSoyadi<<" "<<ogretimelemaniBolum<<" "<<endl;
					ogretimelemaniEkle.close(); 

					cout<<"Yeni ogretim elemani kaydi basarili bir sekilde yapilmistir."<<endl<<"menuye donmek icin lutfen 1 e basiniz...";

					getch();
					system("cls");

					goto ogretimelemani;	

					break;

				}

				case 2://ogretim elemanini sicil No ile arama

				{

					cout<<"OGRETIM ELEMANI  ARAMA "<<endl;
					ifstream ogretimelemaniAra;//dosya okuma ve dosyayi acma 
					ogretimelemaniAra.open("ogrelemani.txt",ios::in);

					int arananSicil;
					cout<<"Ogretim Elemani Sicil No Giriniz:";
					cin>>arananSicil;

					cout<<endl;

					do 

			        { 	

						ogretimelemaniAra>>sicilNo>>ogretimelemaniAdi>>ogretimelemaniSoyadi>>ogretimelemaniBolum; //dosya icindeki degiskenlerin okunmasi

			            if (arananSicil == sicilNo) //girilen deger dosya icersinde mevcut ise bilgiler yazdiriliyor

						{ 

						cout<<" --OGRETIM ELEMANI BILGILERI-- "<<endl;

						cout<<"Ogretim Elemani Sicil No:"<<sicilNo<<endl;
						cout<<"Ogretim Elemani   Adi   :"<<ogretimelemaniAdi<<endl;
						cout<<"Ogretim Elemani Soyadi  :"<<ogretimelemaniSoyadi<<endl;
						cout<<"Ogretim Elemani Bolumu  :"<<ogretimelemaniBolum<<endl;  

						} 

			        } while (!ogretimelemaniAra.eof()); 

			        ogretimelemaniAra.close(); //dosya kapatma
					cout<<"menuye donmek icin lutfen 1 e basiniz...";

					getch();
					system("cls");

					goto ogretimelemani;

					break;

					

				}

				case 3://ogretim elemanlarini listeleme

				{

					cout<<"--OGRETIM ELEMANI LISTELEME-- "<<endl<<endl;

					ifstream ogretimelemaniListele;
					ogretimelemaniListele.open("ogretimelemani.txt",ios::in); 

					string girilenBolum; 

					cout << "Listelenecek bolumu giriniz : "; 
					cin >> girilenBolum;

			        do 

			        { 

			            ogretimelemaniListele>>sicilNo>>ogretimelemaniAdi>>ogretimelemaniSoyadi>>ogretimelemaniBolum; 

			            if (girilenBolum==ogretimelemaniBolum) 

						{ 

							cout<<"Ogretim Elemani Sicil No :"<<sicilNo<<endl;
							cout<<"Ogretim Elemani Adi      :"<<ogretimelemaniAdi<<endl;
							cout<<"Ogretim Elemani Soyadi   :"<<ogretimelemaniSoyadi<<endl;
							cout<<"Ogretim Elemani Bolumu   :"<<ogretimelemaniBolum<<endl<<endl; 

						} 

			        } while (!ogretimelemaniListele.eof()); 

			        ogretimelemaniListele.close(); 

					cout<<"menuye donmek icin lutfen 1 e basiniz...";
					getch();
					system("cls");

					goto ogretimelemani;

					break;

					

				}

				case 4://ogretim elemani bilgilerini duzenleme

				{

					ifstream oku;//okuma yapmak icin
					ofstream yaz;//yazma yapmak icin 

					int duzenleogretimelemani;

					cout<<"Duzenleme yapilacak Ogretim Elamani Sicil No :"; 	
					cin>>duzenleogretimelemani;
					oku.open("ogretimelemani.txt",ios::in);//okunacak dosya aciliyor
					yaz.open("guncellenmis_ogretimelemani.txt",ios::app);//yazilacak dosya aciliyor

					while(!yaz.eof())//dosyanın sonuna kadar okunuyor

					{

						yaz<<sicilNo<<ogretimelemaniAdi<<ogretimelemaniSoyadi<<ogretimelemaniBolum; 

						

					   if(sicilNo == duzenleogretimelemani)

					   {

					   	  	cout<<"Bilgilerinizi Duzenleyin"<<endl;//yeni bilgileri al.
							cout<<"Ogretim Elamani Sicil No   : "; cin>>sicilNo;
							cout<<"Ogretim Elamani Adi  : "; cin>>ogretimelemaniAdi;
							cout<<"Ogretim Elamani Soyad: "; cin>>ogretimelemaniSoyadi;
							cout<<"Ogretim Elamani Bolumu: ";cin>>ogretimelemaniBolum;

					   }

						yaz<<sicilNo<<" "<<ogretimelemaniAdi<<" "<<ogretimelemaniSoyadi<<" "<<ogretimelemaniBolum<<endl;

						//yaz nesnesiyle guncellenmis txt dosyasına yeni bilgiler yaziliyor

					}

					oku.close();//kapatildi
					yaz.close();//kapatildi

					remove("ogretimelemani.txt");//bu dosya silindi
					rename("guncellenmis_ogretimelemani.txt","ogretimelemani.txt");//guncellenmis adli dosyanin adi ogrenci olarak degistirilip kayit ediliyor

					cout<<"Ogretim elamani bilgileri basarili bir sekilde guncellenmistir."<<endl<<"menuye donmek icin lutfen 1 e basiniz...";				 
					getch();
					system("cls");

					goto ogretimelemani;

					break;			 		

				}

				case 5://ana menuye donmek

				{

					goto moduller;

				}

				default:

					cout<<"Lutfen 1 le 5 arasinda bir rakam giriniz "<<endl;

					goto ogretimelemani;

					break;	

			}

			

		}

		case 3://DERS MODULU 

		{

			dersgit:

				dersgit1:

			cout<<" DERS MODULU "<<endl;
			cout<<"1- DERS KAYIT"<<endl;
			cout<<"2- DERS ARAMA"<<endl;
			cout<<"3- DERS LISTELEME"<<endl;
			cout<<"4- DERS BILGILERI DUZENLEME"<<endl;
			cout<<"5- MENUYE DON "<<endl;
			cout<<"  LUTFEN BIR ISLEM SECINIZ: ";cin>>secim;

			system("cls");

			switch(secim)

			{

				case 1://ders kayit

				{

					cout<<" --DERS KAYIT-- "<<endl;

					ofstream dersEkle; 
					dersEkle.open("ders.txt",ios::app);
					cout<<"Dersin Adi      :";cin>>dersAdi;
					cout<<"Dersin Bolumu   :";cin>>dersBolum;

					dersEkle<<dersAdi<<" "<<dersBolum<<" "<<endl;
					dersEkle.close(); 

					cout<<"Yeni ders kaydi basarili bir sekilde yapilmistir."<<endl<<"menuye donmek icin lutfen 1 e basiniz...";

					getch();
					system("cls");

					goto dersgit1;	

					break;

				}

				case 2://ders arama

				{

					cout<<"DERS ARAMA "<<endl;

					ifstream dersAra;//dosya okuma 
					dersAra.open("ders.txt",ios::in);
					string arananDers;

					cout<<"Ders Adi Giriniz:";
					cin>>arananDers;

					cout<<endl;

					do 

			        { 	

						dersAra>>dersAdi>>dersBolum; //dosya icindeki degerler okunuyor

			            if (arananDers == dersAdi) //aranan ders ile ders adi uyusuyorsa

						{ 

						cout<<"--DERS BILGILERI --"<<endl;// ders bilgileri ekrana yazdırılıyor
						cout<<"Ders Adi   :"<<dersAdi<<endl;
						cout<<"Ders Bolumu:"<<dersBolum<<endl;

						} 

			        } while (!dersAra.eof()); 

			        dersAra.close(); //dosya kapatma

					cout<<"menuye donmek icin lutfen 1 e basiniz...";
					getch();
					system("cls");

					goto dersgit;

					break;

				}

				case 3://ders listeleme

				{

					ifstream dersListele;
					dersListele.open("ders.txt",ios::in); 

					string girilenders; 

					cout<<"Listelenecek dersi giriniz : " ; 
					cin>>girilenders;

			        do 

			        { 

			            dersListele>>dersAdi>>dersBolum; 

			            if (girilenders==dersAdi) 

						{ 

							cout<<" --DERS BILGILERI-- "<<endl<<endl;//ders bilgileri listeleniyor
							cout<<"Dersin Adi      :"<<dersAdi<<endl;
							cout<<"Dersin Bolumu   :"<<dersBolum<<endl; 

						} 

			        } while (!dersListele.eof()); 

			        dersListele.close(); 

					cout<<"menuye donmek icin lutfen 1 e basiniz...";
					getch();
					system("cls");

					goto dersgit;

					break;

				}

				case 4://ders bilgileri guncelleme

				{

					ifstream oku;
					ofstream yaz;

					string duzenleDers;

					cout<<"Duzenlenecek dersin adi :"; cin>>duzenleDers;
					oku.open("ders.txt",ios::in);
					yaz.open("guncellenmis_ders.txt",ios::app);

					while(!oku.eof())

					{

					   oku >> dersAdi >> dersBolum ;

					   if(dersAdi == duzenleDers)

					   {

					   	  	cout<<" Yeni Bilgiler "<<endl;//yeni bilgileri al.
							cout<<"Ders Adi   : "; cin>>dersAdi;
							cout<<"Ders Bolumu: "; cin>>dersBolum;

					   }

						yaz<<dersAdi<<" "<<dersBolum<<" "<<endl;

					}

					oku.close();
					yaz.close();

					remove("ders.txt");// ders dosyası siliniyor
					rename("guncellenmis_ders.txt","ders.txt");

					cout<<"Ders bilgileri basarili bir sekilde guncellenmistir."<<endl<<"Ust menuye donmek icin lutfen 1 e basiniz...";				 

					getch();
					system("cls");

					goto dersgit;

					break;

				}

				case 5:

				{

					goto moduller;

					break;

				}

				default:

				cout<<"Lutfen 1 le 5 arasinda rakam giriniz "<<endl;

				goto dersgit;

				break;			

			}
	}
}
}



	

	

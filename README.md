//Hospital Management System with the help of Trees
//Muhammad Talal Akhtar
//DE 36 MTS B
//Final Project DS&Oop

#include<iostream>
#include<string>
using namespace std;

///////////////////////////////////////////////   Patient   ////////////////////////////////////////////////

//*********************Patient Node ********************************
struct Pnode
{
	int srno;    
	string name;
	string gender;
	int age;
	string cateogary;
	string refferedto;
	int charges;
	string remarks;
	Pnode *next;
	Pnode():srno(0),name(""),gender(""),age(0),cateogary(""),refferedto(""),charges(0),remarks(""),next(NULL){}
};

//****************** Patient linkedlist ********************************
struct Plinkedlist
{
private:
	Pnode *head;

public:
	Plinkedlist():head(NULL){}

	bool Pisempty();
	void InsertPatient();
	void Pdisplayall();
	void Psingledisplay();
	void deletepatient(int v);
};
//***********Functions*******************
bool Plinkedlist::Pisempty()
{
	if(head == NULL)
	{return true;}
	else
	{return false;}
}

void Plinkedlist::InsertPatient()
{
	Pnode *ptr = new Pnode;
	string a,b,c,d,e; int f,g;
	cout<<"Name        : ";cin>>a; ptr->name=a;
	cout<<"Gender      : ";cin>>b; ptr->gender=b;
	cout<<"Age         : ";cin>>f; ptr->age=f;
	cout<<"Cateogary   : ";cin>>c; ptr->cateogary=c;
	cout<<"Reffered to : ";cin>>d; ptr->refferedto=d;
	cout<<"Charges     : ";cin>>g; ptr->charges=g;
	cout<<"Remarks     : ";cin>>e; ptr->remarks=e;

	if(Pisempty() == true)
	{
	
	ptr->srno = 1;
		head = ptr;
	}

	else
	{
		Pnode *temp = head;
		
		while(temp->next != NULL)
		{temp = temp->next;}

		ptr->srno = temp->srno+1;
		temp->next = ptr;
		temp = NULL;
	}

}

void Plinkedlist::Pdisplayall()
{
	Pnode *temp = head;
	cout<<"\n****************************PATIENT RECORD*****************************\n";
	while(temp != NULL)
	{
		cout<<"\n***************\n";
		cout<<"PATIENT :"<<temp->srno<<":\n";
		cout<<"***************\n";
	    cout<<"Name        : "<<temp->name<<endl;
	    cout<<"Gender      : "<<temp->gender<<endl;
	    cout<<"Age         : "<<temp->age<<endl;
	    cout<<"Cateogary   : "<<temp->cateogary<<endl;
		cout<<"Charges     : "<<temp->charges<<endl;
	    cout<<"Reffered to : "<<temp->refferedto<<endl;
	    cout<<"Remarks     : "<<temp->remarks<<endl;
		temp = temp->next;
	}
	system("pause");
}

void Plinkedlist::Psingledisplay()
{
	int sr;bool check = 0;
	cout<<"Enter serial no :";cin>>sr;

	Pnode *temp = head;
	while(temp != NULL)
	{
		if(temp->srno == sr)
		{
		cout<<"\n***************\n";
		cout<<"PATIENT :"<<temp->srno<<":\n";
		cout<<"***************\n";
	    cout<<"Name        : "<<temp->name<<endl;
	    cout<<"Gender      : "<<temp->gender<<endl;
	    cout<<"Age         : "<<temp->age<<endl;
	    cout<<"Cateogary   : "<<temp->cateogary<<endl;
		cout<<"Charges     : "<<temp->charges<<endl;
	    cout<<"Reffered to : "<<temp->refferedto<<endl;
	    cout<<"Remarks     : "<<temp->remarks<<endl;
		check++;
		}
		temp = temp->next;
	}

	if(check == 0)
	{
		cout<<"No such record exists!\n";
	}
	system("pause");
}

void Plinkedlist::deletepatient(int sr)
{
	Pnode *temp = head;
	Pnode *temp2 = NULL;
	bool check=0;
	while(temp != NULL)
	{
		if(temp->srno == sr){temp2 = temp;}
		temp = temp->next;
	}

	if(temp2 != NULL)
	{
	if(temp2 == head)
	{
		temp = head;
		head = head->next;
		delete temp;
		temp = NULL;
	}

	else if(temp2->next == NULL)
	{
		temp = head;
		while(temp->next != temp2)
		{temp = temp->next;}
		temp->next = NULL;
		delete temp2;temp2=NULL;temp = NULL;
	}

	else 
	{
		temp = head;
		while(temp->next != temp2)
		{temp = temp->next;}

		temp->next = temp2->next;
		delete temp2; temp2= NULL; temp=NULL;
	}
	}

	else
	{cout<<"\"NO SUCH RECORD EXISTS!\"\n";}
}

//******************* Patient class ********************************
class patient
{
private:
	Plinkedlist p;
public:
	void insertpatient(){p.InsertPatient();}
	void diplayallpatients(){p.Pdisplayall();}
	void displaysinglepatient(){p.Psingledisplay();}
	void deletespecificpient(int sr){p.deletepatient(sr);}
};
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

///////////////////////////////////////////////////////// NURSE ///////////////////////////////////////////////////////

//**********************Nurse Node***************************
struct Nnode
{
	int id;    
	string name;
	string gender;
	int age;
	string department;
	int extradutyhr;
	int salary;
	Nnode *next;
	Nnode():id(0),name(""),gender(""),age(0),department(""),extradutyhr(0),salary(0),next(NULL){}
};


//**********************Nurse Linkedlist**********************
struct Nlinkedlist
{
private:
	Nnode *Nhead;

public:
	Nlinkedlist():Nhead(NULL){}

	bool Nisempty();
	void InsertsNurse();
	void Ndisplayall();
	void Nsingledisplay();
	void deleteNurse(int v);
};
//**********Functions**************
bool Nlinkedlist::Nisempty()
{
	if(Nhead == NULL)
	{return true;}
	else
	{return false;}
}

void Nlinkedlist::InsertsNurse()
{
	Nnode *ptr = new Nnode;
	cout<<"Name          : ";cin>>ptr->name;
	cout<<"ID            : ";cin>>ptr->id;
	cout<<"Gender        : ";cin>>ptr->gender;
	cout<<"Age           : ";cin>>ptr->age;
	cout<<"Department    : ";cin>>ptr->department;
	cout<<"Extra Duty hrs: ";cin>>ptr->extradutyhr;
	cout<<"Salary        : ";cin>>ptr->salary;
	
	if(Nisempty() == true)
	{
			Nhead = ptr;
	}

	else
	{
		Nnode *temp = Nhead;
		
		while(temp->next != NULL)
		{temp = temp->next;}

		temp->next = ptr;
		temp = NULL;
	}

}

void Nlinkedlist::Ndisplayall()
{
	Nnode *temp = Nhead;
	cout<<"\n****************************NURSE RECORD*****************************\n";
	while(temp != NULL)
	{
		cout<<"\n************\n";
		cout<<"NURSE :"<<temp->id<<":\n";
		cout<<"************\n";
	    cout<<"Name           : "<<temp->name<<endl;
	    cout<<"Gender         : "<<temp->gender<<endl;
	    cout<<"Age            : "<<temp->age<<endl;
		cout<<"Department     : "<<temp->department<<endl;
		cout<<"ExtraDutyHours : "<<temp->extradutyhr<<endl;
		cout<<"Salary : "<<temp->salary<<endl;
		temp = temp->next;
	}
	system("pause");
}

void Nlinkedlist::Nsingledisplay()
{
	int sr;bool check = 0;
	cout<<"Enter Nurse ID :";cin>>sr;

	Nnode *temp = Nhead;
	while(temp != NULL)
	{
		if(temp->id == sr)
		{
		cout<<"\n************\n";
		cout<<"NURSE :"<<temp->id<<":\n";
		cout<<"************\n";
	    cout<<"Name           : "<<temp->name<<endl;
	    cout<<"Gender         : "<<temp->gender<<endl;
	    cout<<"Age            : "<<temp->age<<endl;
		cout<<"Department     : "<<temp->department<<endl;
		cout<<"ExtraDutyHours : "<<temp->extradutyhr<<endl;
		cout<<"Salary : "<<temp->salary<<endl;
		check++;
		}
		temp = temp->next;
	}

	if(check == 0)
	{
		cout<<"No such record exists!\n";
	}
	system("pause");
}

void Nlinkedlist::deleteNurse(int sr)
{
	Nnode *temp = Nhead;
	Nnode *temp2 = NULL;
	bool check=0;
	while(temp != NULL)
	{
		if(temp->id == sr){temp2 = temp;}
		temp = temp->next;
	}

	if(temp2 != NULL)
	{
	if(temp2 == Nhead)
	{
		temp = Nhead;
		Nhead = Nhead->next;
		delete temp;
		temp = NULL;
	}

	else if(temp2->next == NULL)
	{
		temp = Nhead;
		while(temp->next != temp2)
		{temp = temp->next;}
		temp->next = NULL;
		delete temp2;temp2=NULL;temp = NULL;
	}

	else 
	{
		temp = Nhead;
		while(temp->next != temp2)
		{temp = temp->next;}

		temp->next = temp2->next;
		delete temp2; temp2= NULL; temp=NULL;
	}
	}

	else
	{cout<<"\"NO SUCH RECORD EXISTS!\"\n";}
}


//**********************Nurse Class****************************
class nurse
{
private:
	Nlinkedlist n;
public:
	void InsertsNurse(){n.InsertsNurse();}
	void diplayallnurses(){n.Ndisplayall();}
	void displaysinglenurse(){n.Nsingledisplay();}
	void deletespecificnurse(int id){n.deleteNurse(id);}
};

////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

////////////////////////////////////////////////////////  Doctor  ///////////////////////////////////////////////////

//************************Doctor Node************************************
struct Dnode
{
	int id;    
	string name;
	string gender;
	int age;
	string field;
	int tasksperformed;
	int income;
	Dnode *next;
	Dnode():id(0),name(""),gender(""),age(0),field(""),tasksperformed(0),income(0),next(NULL){}
};

//************************Doctor Linkedlist******************************
struct Dlinkedlist
{
private:
	Dnode *Dhead;

public:
	Dlinkedlist():Dhead(NULL){}

	bool Disempty();
	void InsertDoctor();
	void Ddisplayall();
	void Dsingledisplay();
	void Deletedoctor(int v);
};
//************Functions***************
bool Dlinkedlist::Disempty()
{
	if(Dhead == NULL)
	{return true;}
	else
	{return false;}
}

void Dlinkedlist::InsertDoctor()
{
	Dnode *ptr = new Dnode;
	cout<<"ID              : ";cin>>ptr->id;
	cout<<"Name            : ";cin>>ptr->name;
	cout<<"Gender          : ";cin>>ptr->gender;
	cout<<"Age             : ";cin>>ptr->age;
	cout<<"Experties       : ";cin>>ptr->field;
	cout<<"Tasks performed : ";cin>>ptr->tasksperformed;
	cout<<"Net Income      : ";cin>>ptr->income;

	if(Disempty() == true)
	{
		Dhead = ptr;
	}

	else
	{
		Dnode *temp = Dhead;
		
		while(temp->next != NULL)
		{temp = temp->next;}

		temp->next = ptr;
		temp = NULL;
	}

}

void Dlinkedlist::Ddisplayall()
{
	Dnode *temp = Dhead;
	cout<<"\n****************************DOCTOR RECORD*****************************\n";
	while(temp != NULL)
	{
		cout<<"\n***************\n";
		cout<<"DOCTOR :"<<temp->id<<":\n";
		cout<<"***************\n";
	    cout<<"Name            : "<<temp->name<<endl;
	    cout<<"Gender          : "<<temp->gender<<endl;
	    cout<<"Age             : "<<temp->age<<endl;
		cout<<"Experties       : "<<temp->field<<endl;
		cout<<"Tasks Performed : "<<temp->tasksperformed<<endl;
		cout<<"NetIncome       : "<<temp->income<<endl;
		temp = temp->next;
	}
	system("pause");
}

void Dlinkedlist::Dsingledisplay()
{
	int sr;bool check = 0;
	cout<<"Enter ID :";cin>>sr;

	Dnode *temp = Dhead;
	while(temp != NULL)
	{
		if(temp->id == sr)
		{
	    cout<<"\n***************\n";
		cout<<"DOCTOR :"<<temp->id<<":\n";
		cout<<"***************\n";
	    cout<<"Name            : "<<temp->name<<endl;
	    cout<<"Gender          : "<<temp->gender<<endl;
	    cout<<"Age             : "<<temp->age<<endl;
		cout<<"Experties       : "<<temp->field<<endl;
		cout<<"Tasks Performed : "<<temp->tasksperformed<<endl;
		cout<<"NetIncome       : "<<temp->income<<endl;
		check++;
		}
		temp = temp->next;
	}

	if(check == 0)
	{
		cout<<"No such record exists!\n";
	}
	system("pause");
}

void Dlinkedlist::Deletedoctor(int sr)
{
	Dnode *temp = Dhead;
	Dnode *temp2 = NULL;
	bool check=0;
	while(temp != NULL)
	{
		if(temp->id == sr){temp2 = temp;}
		temp = temp->next;
	}

	if(temp2 != NULL)
	{
	if(temp2 == Dhead)
	{
		temp = Dhead;
		Dhead = Dhead->next;
		delete temp;
		temp = NULL;
	}

	else if(temp2->next == NULL)
	{
		temp = Dhead;
		while(temp->next != temp2)
		{temp = temp->next;}
		temp->next = NULL;
		delete temp2;temp2=NULL;temp = NULL;
	}

	else 
	{
		temp = Dhead;
		while(temp->next != temp2)
		{temp = temp->next;}

		temp->next = temp2->next;
		delete temp2; temp2= NULL; temp=NULL;
	}
	}

	else
	{cout<<"\"NO SUCH RECORD EXISTS!\"\n";}
}

//************************Doctor Class***********************************
struct doctor
{
	Dlinkedlist d;
	doctor *next;

	doctor():next(NULL){}

	void insertdoctor(){d.InsertDoctor();}
	void diplayalldoctors(){d.Ddisplayall();}
	void displaysingledoctor(){d.Dsingledisplay();}
	void deletespecificdoctor(int sr){d.Deletedoctor(sr);}
};
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

/////////////////////////////////////////////////// HOSPITAL ///////////////////////////////////////////////////////
class hospital
{
private:
	doctor RMO,LMO,Opti,Dent,Physi,Surg,Mater;
	nurse dept, general;
	patient outdoor,operation,underexam;

public:
	void addDoctor();
	void addNurse();
	void addPatient();

	void DisplayAllDoctors();
	void DisplayAllNurses();
	void DisplayAllPatients();

	void DisplaySingleDoctor();
	void DisplaySingleNurse();
	void DisplaySinglePatient();

	void DeleteSpecificDoctor();
	void DeleteSpecificNurse();
	void DeleteSpecificPatient();
};
//******** Add record Function****************
void hospital::addDoctor()
{
	int choice; 
	cout<<"Which doctor record do you want to enter:";
	cout<<"RMO = 1; LMO = 2; Optician = 3; Dentist = 4; Physiotherapist = 5; Surgeon = 6; Maternity = 7\n";
	cin>>choice;

	switch (choice)
	{
	case 1:
		RMO.insertdoctor();
		break;
    case 2:
		LMO.insertdoctor();
		break;
	case 3:
		Opti.insertdoctor();
		break;
	case 4:
		Dent.insertdoctor();
		break;
	case 5:
		Physi.insertdoctor();
		break;
	case 6:
		Surg.insertdoctor();
		break;
	case 7:
		Mater.insertdoctor();
		break;
	default:
		cout<<"Invalid Input....!\n";
		break;
	}
}

void hospital::addNurse()
{
	int choice; 
	cout<<"Which Nurse record do you want to enter:";
	cout<<"Department = 1; General = 2;\n";
	cin>>choice;

	switch(choice)
	{
	case  1:
		dept.InsertsNurse();
		break;
	case 2:
		general.InsertsNurse();
		break;
	default:
		cout<<"Invalid Input....!\n";
		break;
	}
}

void hospital::addPatient()
{
	
	int choice; 
	cout<<"Which Patient record do you want to enter:";
	cout<<"Outdoor = 1; Operation = 2; Under-Examination = 3;\n";
	cin>>choice;

	switch(choice)
	{
	case 1:
		outdoor.insertpatient();
		break;
	case 2:
		operation.insertpatient();
		break;
	case 3:
		underexam.insertpatient();
		break;
	default:
		cout<<"Invalid Input......!\n";
	}
}

//************ Display All Function **********************
void hospital::DisplayAllDoctors()
{
	int choice; 
	cout<<"Which cateogary of Doctors do you want to see (All doctors record of the cateogary)\n:";
	cout<<"RMO = 1; LMO = 2; Optician = 3; Dentist = 4; Physiotherapist = 5; Surgeon = 6; Maternity = 7\n";
	cin>>choice;

	switch (choice)
	{
	case 1:
		RMO.diplayalldoctors();
		break;
    case 2:
		LMO.diplayalldoctors();
		break;
	case 3:
		Opti.diplayalldoctors();
		break;
	case 4:
		Dent.diplayalldoctors();
		break;
	case 5:
		Physi.diplayalldoctors();
		break;
	case 6:
		Surg.diplayalldoctors();
		break;
	case 7:
		Mater.diplayalldoctors();
		break;
	default:
		cout<<"Invalid Input....!\n";
		break;
	}
}

void hospital::DisplayAllNurses()
{
	int choice; 
	cout<<"Which cateogary of Nurses do you want to see (All doctors record of the cateogary)\n:";
	cout<<"Department = 1; General = 2;\n";
	cin>>choice;

	switch(choice)
	{
	case  1:
		dept.diplayallnurses();
		break;
	case 2:
		general.diplayallnurses();
		break;
	default:
		cout<<"Invalid Input....!\n";
		break;
	}
}

void hospital::DisplayAllPatients()
{
	
	int choice; 
	cout<<"Which cateogary of Patients do you want to see (All doctors record of the cateogary)\n:";
	cout<<"Outdoor = 1; Operation = 2; Under-Examination = 3;\n";
	cin>>choice;

	switch(choice)
	{
	case 1:
		outdoor.diplayallpatients();
		break;
	case 2:
		operation.diplayallpatients();
		break;
	case 3:
		underexam.diplayallpatients();
		break;
	default:
		cout<<"Invalid Input......!\n";
	}
}

//************** Display Single Function *****************
void hospital::DisplaySingleDoctor()
{
	int choice; 
	cout<<"First chose the cateogary of Doctor then wrote ID to find the specific record\n:";
	cout<<"RMO = 1; LMO = 2; Optician = 3; Dentist = 4; Physiotherapist = 5; Surgeon = 6; Maternity = 7\n";
	cin>>choice;

	switch (choice)
	{
	case 1:
		RMO.displaysingledoctor();
		break;
    case 2:
		LMO.displaysingledoctor();
		break;
	case 3:
		Opti.displaysingledoctor();
		break;
	case 4:
		Dent.displaysingledoctor();
		break;
	case 5:
		Physi.displaysingledoctor();
		break;
	case 6:
		Surg.displaysingledoctor();
		break;
	case 7:
		Mater.displaysingledoctor();
		break;
	default:
		cout<<"Invalid Input....!\n";
		break;
	}
}

void hospital::DisplaySingleNurse()
{
	int choice; 
	cout<<"First chose the cateogary of Nurse then wrote ID to find the specific record\n:";
	cout<<"Department = 1; General = 2;\n";
	cin>>choice;

	switch(choice)
	{
	case  1:
		dept.displaysinglenurse();
		break;
	case 2:
		general.displaysinglenurse();
		break;
	default:
		cout<<"Invalid Input....!\n";
		break;
	}
}

void hospital::DisplaySinglePatient()
{
	
	int choice; 
	cout<<"First chose the cateogary of Patient then wrote ID to find the specific record\n:";
	cout<<"Outdoor = 1; Operation = 2; Under-Examination = 3;\n";
	cin>>choice;

	switch(choice)
	{
	case 1:
		outdoor.displaysinglepatient();
		break;
	case 2:
		operation.displaysinglepatient();
		break;
	case 3:
		underexam.displaysinglepatient();
		break;
	default:
		cout<<"Invalid Input......!\n";
	}
}

//************ Delete specific Function ****************
void hospital::DeleteSpecificDoctor()
{
	int choice; int id;
	cout<<"First chose the cateogary of Doctor then wrote ID to delete the specific record\n:";
	cout<<"RMO = 1; LMO = 2; Optician = 3; Dentist = 4; Physiotherapist = 5; Surgeon = 6; Maternity = 7\n";
	cin>>choice;
	cout<<"Enter ID : ";cin>>id;

	switch (choice)
	{
	case 1:
		RMO.deletespecificdoctor(id);
		break;
    case 2:
		LMO.deletespecificdoctor(id);
		break;
	case 3:
		Opti.deletespecificdoctor(id);
		break;
	case 4:
		Dent.deletespecificdoctor(id);
		break;
	case 5:
		Physi.deletespecificdoctor(id);
		break;
	case 6:
		Surg.deletespecificdoctor(id);
		break;
	case 7:
		Mater.deletespecificdoctor(id);
		break;
	default:
		cout<<"Invalid Input....!\n";
		break;
	}
}

void hospital::DeleteSpecificNurse()
{
	int choice; int id;
	cout<<"First chose the cateogary of Nurse then wrote ID to delete the specific record\n:";
	cout<<"Department = 1; General = 2;\n";
	cin>>choice;
	cout<<"Enter ID : ";cin>>id;

	switch(choice)
	{
	case  1:
		dept.deletespecificnurse(id);
		break;
	case 2:
		general.deletespecificnurse(id);
		break;
	default:
		cout<<"Invalid Input....!\n";
		break;
	}
}

void hospital::DeleteSpecificPatient()
{
	
	int choice; int sr;
	cout<<"First chose the cateogary of Patient then wrote Sr No. to delete the specific record\n:";
	cout<<"Outdoor = 1; Operation = 2; Under-Examination = 3;\n";
	cin>>choice;
	cout<<"Enter Serial No.: ";cin>>sr;

	switch(choice)
	{
	case 1:
		outdoor.deletespecificpient(sr);
		break;
	case 2:
		operation.deletespecificpient(sr);
		break;
	case 3:
		underexam.deletespecificpient(sr);
		break;
	default:
		cout<<"Invalid Input......!\n";
	}
}

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

////////////////////////////////////////////////////////main Function/////////////////////////////////////////////////
void main()
{
	hospital h; int choice=0;

	while(choice != 5)
	{
	cout<<"\n\t*********************************************************\n";
	cout<<"\n\t  WELCOME TO REHAN'S HOSPITAL RECORD MANAGEMENT SERVICE\n";
	cout<<"\n\t*********************************************************\n\n";

	cout<<"\t\t\t      INSTRUCTIONS\n";
	cout<<"-------------------------------------------------------------------------------\n\n";
	cout<<"1-  Inorder to add record press =                            1\n";
	cout<<"2-  Inorder to examine single record press =                 2\n";
	cout<<"3-  Inorder to examine a record of a whole cateogary press = 3\n";
	cout<<"4-  Inorder to delete specific recorrd press =               4\n";
	cout<<"5- to exit system press ** 5 ** \n";
	cout<<"-------------------------------------------------------------------------------\n\n";
	cout<<"COMMAND = ";cin>>choice;
	system("cls");

	
	switch(choice)
	{
	case 1:
		{
			int ch=0;
			cout<<"\n\t****************************************************\n";
	        cout<<"\n\t  WELCOME TO RECORD BRANCH OF HOSPITAL SERVICE\n";
	        cout<<"\n\t*****************************************************\n\n";

			cout<<"1- For Entering Record of Doctor , press = 1\n";
			cout<<"2- For Entering Record of Nurse  , press = 2\n";
			cout<<"3- For Entering Record of Patient, press = 3\n";
			cout<<"4- Press 4 to back\n\n";
			cout<<"CHOICE :";cin>>ch;

			switch(ch)
			{
			case 1:
				h.addDoctor();break;
			case  2:
				h.addNurse();break;
			case 3:
				h.addPatient();break;
			case 5:
				break;
			default:
				cout<<"Invalid Input......!\n";
			}
		}
		break;
	case 2:
		{
			int ch=0;
			cout<<"\n\t******************************************************\n";
	        cout<<"\n\t  WELCOME TO SNGLE SEARCH BRANCH OF HOSPITAL SERVICE\n";
	        cout<<"\n\t*******************************************************\n\n";

			cout<<"1- For Searhing Record of 1 Doctor , press = 1\n";
			cout<<"2- For Searhing Record of 1 Nurse  , press = 2\n";
			cout<<"3- For Searhing Record of 1 Patient, press = 3\n";
			cout<<"4- Press 4 to back\n\n";
			cout<<"CHOICE :";cin>>ch;

			switch(ch)
			{
			case 1:
				h.DisplaySingleDoctor();break;
			case  2:
				h.DisplaySingleNurse();break;
			case 3:
				h.DisplaySinglePatient();break;
			case 5:
				break;
			default:
				cout<<"Invalid Input......!\n";
			}
		}
		break;
	case 3:
		{
			int ch=0;
			cout<<"\n\t******************************************************\n";
	        cout<<"\n\t  WELCOME TO ALL SEARCH BRANCH OF HOSPITAL SERVICE\n";
	        cout<<"\n\t*******************************************************\n\n";

			cout<<"1- For Searhing Record of a cteogarry of Doctors , press = 1\n";
			cout<<"2- For Searhing Record of a cteogarry of Nurses  , press = 2\n";
			cout<<"3- For Searhing Record of a cteogarry of Patients, press = 3\n";
			cout<<"4- Press 4 to back\n\n";
			cout<<"CHOICE :";cin>>ch;

			switch(ch)
			{
			case 1:
				h.DisplayAllDoctors();break;
			case  2:
				h.DisplayAllNurses();break;
			case 3:
				h.DisplayAllPatients();break;
			case 5:
				break;
			default:
				cout<<"Invalid Input......!\n";
			}
		}
		break;
	case 4:
		{
			int ch=0;
			cout<<"\n\t*************************************************************\n";
	        cout<<"\n\t  WELCOME TO SNGLE DELETE RECORD BRANCH OF HOSPITAL SERVICE\n";
	        cout<<"\n\t*************************************************************\n\n";

			cout<<"1- For Deleting Record of 1 Doctor , press = 1\n";
			cout<<"2- For Deleting Record of 1 Nurse  , press = 2\n";
			cout<<"3- For Deleting Record of 1 Patient, press = 3\n";
			cout<<"4- Press 4 to back\n\n";
			cout<<"CHOICE :";cin>>ch;

			switch(ch)
			{
			case 1:
				h.DeleteSpecificDoctor();break;
			case  2:
				h.DeleteSpecificNurse();break;
			case 3:
				h.DeleteSpecificPatient();break;
			case 5:
				break;
			default:
				cout<<"Invalid Input......!\n";
			}
		}
		break;
	case 5:
		break;

	default:
		cout<<"\n\t    Invalid Input......!\n\t";system("pause");
		break;
	}
	system("cls");
	}
	cout<<"\n\n\t     THANKS FOR USING OUR SERVICES.........!\n\n\t\t";
}

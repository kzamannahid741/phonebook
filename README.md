#include <stdio.h>
#include <stdlib.h>
#include <string.h>


struct person
{
    char name[30];
    char country_code[4];
    long int mble_no;
    char sex[8];
    char mail[100];
};

// Defining person data type.
typedef struct person person;

// All function declaration.
void remove_all();
void print_menu();
void add_person();
void list_record();
void search_person();
void remove_person();
void update_person();
void take_input(person *p);

int n;
void login();

// Program starts here.
int main_menu()
{
    print_menu();
    return 0;
}


// This function will start our program.
int public ;
int main()
{
    int choice;
    login();

    while(1)
    {
        print_menu();
        scanf("%d",&choice);
        switch(choice)
        {
        case 1:
            list_record();
            getchar();
            getchar();
            break;
        case 2:
            add_person();
            getchar();
            getchar();
            break;
        case 3:
            search_person();
            getchar();
            getchar();
            break;
        case 4:
            remove_person();
            getchar();
            getchar();
            break;
        case 5:
            update_person();
            getchar();
            getchar();
            break;
        case 6:
            remove_all();
            getchar();
            getchar();
            break;
        default :
            system("clS");
            printf("Thanks for using phonebook visit again : )\n");
            getchar();
            getchar();
            exit(1);
        }
    }
}

void login()
{

    int valid=0;
    int n,p, i=0;
    char uname[20], a;
    char pword[10];


    printf("\n");
    printf("\n");
    printf("\n");
    printf("\n");
    printf("\n");
    printf("\n");
    printf("\n");
    printf("\t\t\t\t**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**\n");
    printf("\t\t\t\t**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**\n");
    printf("\t\t\t\t       ==================================================\n");
    printf("\t\t\t\t       =                                                =\n");
    printf("\t\t\t\t       =                                                =\n");
    printf("\t\t\t\t       =           WELCOME TO OUR PHONEBOOK             =\n");
    printf("\t\t\t\t       =                                                =\n");
    printf("\t\t\t\t       =                                                =\n");
    printf("\t\t\t\t       ==================================================\n");
    printf("\t\t\t\t**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**\n");
    printf("\t\t\t\t**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**\n\n");

    printf("\n\n");

    printf("\t\t\t\tPlease Enter Your UserName & Password : \n\n");

    printf("\t\t\t\tUser Name:  ");
    scanf("%s",uname);
    printf("\n");
    printf("\t\t\t\tPassword:  ");
    scanf("%s", pword);


    n = strcmp("BUBT",uname);
    p = strcmp("SDP-1",pword);
    if(n == 0 && p == 0)
    {
        printf("\n\t\t\t\tLogin successful.\n");
        getch();

    }
    else
    {

        printf("\n\t\t\t\tWrong Password. Please Enter Valid Password And User Name\n");
        getch();
        system("cls");
        login();

    }

    printf("\n\t\t\t\tPress any key to continue....\n");
    getch();
}

// This will print main menu.
void print_menu()
{

    system("cls");
    printf("\t\t\t\t**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**\n");
    printf("\t\t\t\t**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**\n");
    printf("\t\t\t\t       ==================================================\n");
    printf("\t\t\t\t       =                                                =\n");
    printf("\t\t\t\t       =                                                =\n");
    printf("\t\t\t\t       =           WELCOME TO OUR PHONEBOOK             =\n");
    printf("\t\t\t\t       =                                                =\n");
    printf("\t\t\t\t       =                                                =\n");
    printf("\t\t\t\t       ==================================================\n");
    printf("\t\t\t\t **-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**\n");
    printf("\t\t\t\t **-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**\n\n");

    int getch();
    printf("\n");
    printf("\n");
    printf("\n");
    printf("\t\t\t1. List record\n\n");
    printf("\t\t\t2. Add person\n\n");
    printf("\t\t\t3. Search person Details\n\n");
    printf("\t\t\t4. Remove person\n\n");
    printf("\t\t\t5. Update person\n\n");
    printf("\t\t\t6. Delete all contacts\n\n");
    printf("\t\t\t7. Exit Phonebook\n\n\n");

    printf("\t\t\t\tEnter your Choice : ");
}

// This function will add contact into phonebook.
void add_person()
{
    system("cls");
    FILE *fp;
    fp = fopen("phonebook_db", "ab+");
    if (fp == NULL)
    {
        printf("Error in file opening, Please try again !\n\n");
        printf("Press any key to continue....\n");
        return;
    }
    else
    {
        person p;
        take_input(&p);
        fwrite(&p, sizeof(p), 1, fp);
        fflush(stdin);
        fclose(fp);
        system("cls");
        printf("Record added Successfully\n\n");
        printf("Press any key to continue ....\n");

    }
}

// By this we take contact information.
void take_input(person *p)
{
    system("cls");
    getchar();
    printf("Enter name : ");
    scanf("%[^\n]s",p->name);

    printf("Enter country code : ");
    scanf("%s",p->country_code);

    printf("Enter mobile no : ");
    scanf("%ld",&p->mble_no);

    printf("Enter sex : ");
    scanf("%s",p->sex);

    printf("Enter email : ");
    scanf("%s",p->mail);

}

// This function will list contact available in phonebook.
void list_record()
{
    system("cls");
    FILE *fp;
    fp = fopen("phonebook_db", "rb");
    if (fp == NULL)
    {
        printf("Error in file opening, Please try again !\n");
        printf("Press any key to continue....\n");
        return;
    }
    else
    {
        person p;
        printf("\t\t\t\t******************************************************************************\n");
        printf("\t\t\t\t*                  Here is all records listed in phonebook                   *\n");
        printf("\t\t\t\t******************************************************************************\n\n\n");
        printf("NAME\t\t\t\t   COUNTRY CODE\t\t    PHONE NO\t\t    SEX\t\t             EMAIL\n");
        printf("\n---------------------------------------------------------------------------------------------------------------------------------------------\n");


        while (fread(&p, sizeof(p), 1, fp) == 1)
        {
            int i;
            int len1 = 40 - strlen(p.name);
            int len2 = 19 - strlen(p.country_code);
            int len3 = 15;
            int len4 = 21 - strlen(p.sex);
            printf("%s",p.name);
            for(i=0; i<len1; i++)
                printf(" ");

            printf("%s",p.country_code);
            for(i=0; i<len2; i++)
                printf(" ");

            printf("%ld",p.mble_no);
            for(i=0; i<len3; i++)
                printf(" ");

            printf("%s",p.sex);
            for(i=0; i<len4; i++)
                printf(" ");

            printf("%s",p.mail);
            printf("\n");
            fflush(stdin);
        }
        fflush(stdin);
        fclose(fp);
        printf("\n\nPress any key to continue....\n");

    }
}

// This function will search contact in phonebook.
void search_person()
{
    system("cls");
    long int phone;
    printf("Enter Phone number of the person you want to search : ");
    scanf("%ld",&phone);

    FILE *fp;
    fp = fopen("phonebook_db", "rb");
    if (fp == NULL)
    {
        printf("Error in file opening, Please try again !\n");
        printf("Press any key to continue....\n");
        return;
    }
    else
    {
        int flag = 0;
        person p;
        while (fread(&p, sizeof(p), 1, fp) == 1)
        {
            if(p.mble_no == phone)
            {
                printf("NAME\t\t\t\t   COUNTRY CODE\t\t    PHONE NO\t\t    SEX\t\t             EMAIL\n");
                printf("---------------------------------------------------------------------------------------------------------------------------------------------\n");
                int i;
                int len1 = 40 - strlen(p.name);
                int len2 = 19 - strlen(p.country_code);
                int len3 = 15;
                int len4 = 21 - strlen(p.sex);
                printf("%s",p.name);
                for(i=0; i<len1; i++)
                    printf(" ");

                printf("%s",p.country_code);
                for(i=0; i<len2; i++)
                    printf(" ");

                printf("%ld",p.mble_no);
                for(i=0; i<len3; i++)
                    printf(" ");

                printf("%s",p.sex);
                for(i=0; i<len4; i++)
                    printf(" ");

                printf("%s",p.mail);
                printf("\n");

                flag = 1;
                break;
            }
            else
                continue;

        }
        if(flag == 0)
        {
            system("cls");
            printf("Person is not in the Phonebook\n");
        }
        fflush(stdin);
        fclose(fp);
        printf("\n\nPress any key to continue....\n");
    }

}

// This function will remove contact from phonebook.
void remove_person()
{
    system("cls");
    long int phone;
    printf("Enter Phone number of the person you want to remove from phonebook : ");
    scanf("%ld",&phone);

    FILE *fp,*temp;
    fp = fopen("phonebook_db", "rb");
    temp = fopen("temp","wb+");
    if (fp == NULL)
    {
        printf("Error in file opening, Plz try again !\n");
        printf("Press any key to continue....\n");
        return;
    }
    else
    {
        person p;
        int flag = 0;
        while (fread(&p, sizeof(p), 1, fp) == 1)
        {
            if(p.mble_no == phone)
            {
                system("cls");
                printf("Person removed successfully\n");
                flag = 1;
            }
            else
                fwrite(&p,sizeof(p),1,temp);
            fflush(stdin);
        }
        if(flag == 0)
        {
            system("cls");
            printf("No record found for %ld number\n",phone);
        }
        fclose(fp);
        fclose(temp);
        remove("phonebook_db");
        rename("temp","phonebook_db");
        fflush(stdin);
        printf("Press any key to continue....\n");

    }

}

// This function will update contact information.
void update_person()
{

    system("cls");
    long int phone;
    printf("Enter Phone number of the person you want to update details : ");
    scanf("%ld",&phone);

    FILE *fp,*temp;
    fp = fopen("phonebook_db", "rb");
    temp = fopen("temp","wb+");
    if (fp == NULL)
    {
        printf("Error in file opening, Plz try again !\n");
        printf("Press any key to continue....\n");
        return;
    }
    else
    {
        int flag = 0;
        person p;
        while (fread(&p, sizeof(p), 1, fp) == 1)
        {
            if(p.mble_no == phone)
            {
                take_input(&p);
                fwrite(&p, sizeof(p), 1, temp);
                system("cls");
                printf("Data updated successfully\n");
                flag = 1;
            }
            else
                fwrite(&p,sizeof(p),1,temp);
            fflush(stdin);
        }
        if(flag == 0)
        {
            system("cls");
            printf("No record found for %ld number\n",phone);
        }
        fclose(fp);
        fclose(temp);
        remove("phonebook_db");
        rename("temp","phonebook_db");
        fflush(stdin);
        printf("Press any key to continue....\n");
    }
}


// This function will clear all the data of phonebook.
void remove_all()
{
    char choice;
    system("cls");
    remove("./phonebook_db");
    printf("All data in the phonebook deleted successfully\n");
    printf("Press any key to continue ... \n");
}

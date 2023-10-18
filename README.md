#include <stdio.h>
#include <string.h>
#include <ctype.h>

#define BOYUT 50

void TerstenYazimKarsılastırma(char metin[])
{
	int say = 0;
	for (int i = 0; i < strlen(metin); i++)
	{
		if (isalpha(metin[i]))
		{
			metin[say] = toupper(metin[i]);
			say++;
		}
	}
	metin[say] = '\0';

	int flag = 1;
	for (int i = 0; i < strlen(metin) / 2; i++)
	{
		if (metin[i] != metin[strlen(metin) - i - 1])
		{
			flag = 0;
			printf("\033[31mKELIME POLINDROM DEGIL\033[0m\n");
			break;
		}
	}

	if (flag)
		printf("\033[36mKELIME POLINDROM\033[0m\n");
}

int main()
{
	printf("Turkce Karakter Girmeyiniz\n\n");
	char metin[BOYUT];

	printf("Metin girin:");
	fgets(metin, sizeof(metin), stdin);
	metin[strcspn(metin, "\n")] = '\0';


	printf("\n\n");
	TerstenYazimKarsılastırma(metin);
	printf("\n\n");


	return 0;
}


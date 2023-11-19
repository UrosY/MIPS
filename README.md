# MIPS
Projekat Iz MIPS-a
Prvi korak je izdara šeme u Proteusu.
Koristimo STM32F103C6. Granu sa diodom i otpornikom povezujemo na port "B" i to na pin 2. 
-Port je izabran na osnovu toga što je borj samoglasnika u meme imenu manji od broja suglasnika.
Uroš Zdravković ---> 5 samoglasnika  9 suglasnika    9 > 5 ==> port B
-Pin je odabran na osnovu toga kada se sabere broj slova u imenu i prezimenu uradi moguo od 6
Uroš Zdravković ---> 14 slova   14 % 6 = 2 ==> pin = 2
Drugi korak je izrada koda u STM32CubeIDE
Biramo STM32F103C6 podešavamo clock.
KOD-------------------------------------
while (1) // beskonačna petlja
	      {
	          for(int i = 0; i < 4; i++) //broj ponavljanja impulsa u prvom cikulusu je broj slova u imenu. Sadržaj for petlje se ponavlja 4 puta
	          {
	              HAL_GPIO_WritePin(GPIOB, GPIO_PIN_2, GPIO_PIN_SET);
	              HAL_Delay(4);
	              HAL_GPIO_WritePin(GPIOB, GPIO_PIN_2, GPIO_PIN_RESET);
	              HAL_Delay(10);
	          }
	          for(int i = 0; i < 10; i++) //broj ponavljanja impulsa u drugom ciklusu je broj slova u prezimenu. Sadržaj for petlje se ponavlja 10 puta
	          {
	              HAL_GPIO_WritePin(GPIOB, GPIO_PIN_2, GPIO_PIN_SET);
	              HAL_Delay(10);
	              HAL_GPIO_WritePin(GPIOB, GPIO_PIN_2, GPIO_PIN_RESET);
	              HAL_Delay(4);
	          }
	      }

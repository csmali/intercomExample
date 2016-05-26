#include <stdio.h>
#include <string.h>
#include <sys/types.h>
#include <sys/ipc.h>
#include <sys/shm.h>
#define SHM_KEY 1234567
int main(void)
{
	char *padr;
	char *x;
	char line[50];
	int shmid;
	int shmid2;
	if ((shmid = shmget(SHM_KEY, 1024, IPC_CREAT|0666)) < 0) {
		perror("shmget");
		exit(1);
	}
	if ((padr = (char *) shmat(shmid, NULL, 0)) == (void *) -1) {
		perror("shmat");
		exit(1);
	}
		
	
	strcpy(padr,""); // memoryde son kalan char dizisini siliyor quit varsa kullanilamaz durumda olurdu cunku

	while(1){
		scanf("%s",line);
		strcpy(padr,line);
		*(padr+1000)='w';   // yazildi flagi
		if(strcmp(padr,"quit")==0){
			break;		
		}
	}
	
	
	shmdt(padr);
	shmctl(shmid, IPC_RMID, NULL);
	return 0;
}

#include<stdio.h>
#include<dirent.h>
#include<string.h>
int main()
{
int ct=0,line=1;
char c,word[10],a,buf[10];
FILE *fp;
 struct dirent*de;
DIR *dr=opendir("C:\\Users\\ADITI THAKUR\\Desktop\\Z");
 if(dr==NULL)
 {
printf("No");
return 0;
 }
 printf("Enter word to search\n");
             scanf("%s",&word);

while((de=readdir(dr))!=NULL)
 {
  printf("\n%s\n",de->d_name);
 if (!strcmp (de->d_name,"."))
            continue;
        if (!strcmp (de->d_name,".."))
            continue;
            fp=fopen(de->d_name,"r");
            {
            if(fp==NULL)
             printf("Empty");
             else
             {
int result;
c=fgetc(fp);
       while((fscanf(fp,"%s",buf)!= EOF)||(c!=EOF))
         {

          ct++;
          result=strcmp(word,buf);
          if(c=='\n')
          {
           line++;
           ct=1;
          }

         if(result==0)
         {
          printf("Word found at position %d and at %d line\n",ct,line);
          break;
         }
c=fgetc(fp);
         }
         if(result!=0)
          printf("Word not found\n");
line=1;
ct=0;
  }
  fclose(fp);

}
}
  closedir(dr);
 return 0;
}




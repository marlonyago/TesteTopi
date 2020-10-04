# Teste Topi


Logo abaixo estão algumas especificações, principalmente relacionado ao Objeto .

# Custom Objects

**Name**: Repositories Git
**API Name**: RepositoriesGit__c

| Fields | Type |
| ------ | ------ |
| BodyJson__c | Long Text Area(32768) |
| Forks__c | Number(18, 0) |
| Id_Git__c | Number(18, 0) |
| language__c | Picklist |
| Last_update__c | Date/Time |
| Owner_id__c | Number(18, 0) |
| Owner_html_url__c | URL(255) |
| Owner_login__c | Text(255) |
| Owner_node_id__c | Text(150) |
| Repositorie__c | URL(255) |
| Stars__c  | Number(16, 0) |
| User__c | Lookup(User) |

**Name**: Callout Error
**API Name**: CalloutError__c

| Fields | Type |
| ------ | ------ |
| Name  | Auto Number |
| Endpoint__c | Text(255) |
| Method__c  | Text(255) |
| RequestBody__c | Text Area(255) |
| RequestDateTime__c | Date/Time |
| ResponseBody__c  | Long Text Area(131072) |
| ResponseStatusCode__c  |  Number(3, 0) |

# Schedulable

Código para ser rodado todo dia as 6 horas da manhã
```sh
System.schedule('Get List Github', '0 0 6 ? * *',
new SchedulableGit_Repositorie(null));
```

Se preferir pode rodar esse que roda no mesmo dia uma vez no prazo de 10 minutos e fica programando para o dia seguinte no mesmo horário.
```sh
String hour = String.valueOf(Datetime.now().hour());
String min = String.valueOf(Datetime.now().minute() + 10); 
String ss = String.valueOf(Datetime.now().second());

//parse to cron expression
String nextFireTime = ss + ' ' + min + ' ' + hour + ' * * ?';

SchedulableGit_Repositorie s = new SchedulableGit_Repositorie(); 
System.schedule('Get List Githu' + String.valueOf(Datetime.now()), nextFireTime, s);
```

 ## Class Test

A seguir a porcentagem de cover de cada classe:

| Class | % |
| ------ | ------ |
|Git_Items| 100
|ControllerRepositorie| 100
|SchedulableGit_Repositorie| 94
|SendRequest| 100
|ApexSharing| 82
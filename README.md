# ORPROJECT1
// model file
/*********************************************
 * OPL 22.1.1.0 Model
 * Author: Shashank
 * Creation Date: 05-Apr-2023 at 1:51:14 PM
 *********************************************/
/*********************************************
 * OPL 22.1.1.0 Model
 * Author: Dell
 * Creation Date: 29-Mar-2023 at 7:43:35 PM
 *********************************************/
int N = ...;
int X = ...;

range num=1..N;

dvar int+ x[1..N];

float Calories[1..N] = ...;
float Cholestrol[1..N] = ...;
float Fat[1..N] = ...;
float Sodium[1..N] = ...;
float Carbohydrate[1..N] = ...;
float Dietary_Fiber[1..N] = ...;
float Protein[1..N] = ...;
float Vit_A[1..N] = ...;
float Vit_C[1..N] = ...;
float Calcium[1..N] = ...;
float Iron[1..N] = ...;
int CheckBox[1..N] = ...;
float cost[1..N] = ...;
float min_serve[1..N] = ...;
float max_serve[1..N] = ...;
float A[1..X] = ...;
float B[1..X] = ...;

string Names[1..N]=...;

minimize sum (i in 1..N)x[i]*cost[i];

subject to {
  forall(i in 1..N)if(CheckBox[i] == 0)
    {
      x[i] == 0;
    }
    
 
 forall(i in 1..N) x[i]>= min_serve[i];
 forall(i in 1..N) x[i] <= max_serve[i];
 sum(i in 1..N) Calories[i]*x[i] >= A[1];
 sum(i in 1..N) Calories[i]*x[i] <=B[1];
 sum(i in 1..N) Cholestrol[i]*x[i] >=A[2];
 sum(i in 1..N) Cholestrol[i]*x[i] <=B[2];
 sum(i in 1..N) Fat[i]*x[i] >= A[3];
 sum(i in 1..N) Fat[i]*x[i] <=B[3];
 sum(i in 1..N) Sodium[i]*x[i] >= A[4];
 sum(i in 1..N) Sodium[i]*x[i] <= B[4];
 sum(i in 1..N) Carbohydrate[i]*x[i] >= A[5];
 sum(i in 1..N) Carbohydrate[i]*x[i] <=B[5];
 sum(i in 1..N) Dietary_Fiber[i]*x[i] >= A[6];
 sum(i in 1..N) Dietary_Fiber[i]*x[i] <=B[6];
 sum(i in 1..N) Protein[i]*x[i] >= A[7];
 sum(i in 1..N) Protein[i]*x[i] <= B[7];
 sum(i in 1..N) Vit_A[i]*x[i] >= A[8];
 sum(i in 1..N) Vit_A[i]*x[i] <= B[8];
 sum(i in 1..N) Vit_C[i]*x[i] >= A[9];
 sum(i in 1..N) Vit_C[i]*x[i] <= B[9];
 sum(i in 1..N) Calcium[i]*x[i] >= A[10];
 sum(i in 1..N) Calcium[i]*x[i] <=B[10];
 sum(i in 1..N) Iron[i]*x[i] >= A[11];
 sum(i in 1..N) Iron[i]*x[i] <=B[11];
 
 }
 
 
execute {
	for (var i in num) if (x[i]!=0) writeln(Names[i],"->",x[i]);
}

//dat file
/*********************************************
 * OPL 22.1.1.0 Data
 * Author: Shashank
 * Creation Date: 05-Apr-2023 at 1:51:14 PM
 *********************************************/
/*********************************************
 * OPL 22.1.1.0 Data
 * Author: Dell
 * Creation Date: 29-Mar-2023 at 7:43:35 PM
 *********************************************/
SheetConnection
 projectdata("C:\\Users\\Shashank\\Downloads\\DIET.xlsx");
 N = 64;
 Calories from
 SheetRead(projectdata,"Calories");
  Cholestrol from
 SheetRead(projectdata,"Cholesterol");
  Fat from
 SheetRead(projectdata,"Total_Fat");
   Sodium from
 SheetRead(projectdata,"Sodium");
   Carbohydrate from
 SheetRead(projectdata,"Carbohydrates");
   Dietary_Fiber from
 SheetRead(projectdata,"Dietary_Fiber");
   Protein from
 SheetRead(projectdata,"Protein");
   Vit_A from
 SheetRead(projectdata,"Vit_A");
   Vit_C from
 SheetRead(projectdata,"Vit_C");
   Calcium from
 SheetRead(projectdata,"Calcium");
   Iron from
 SheetRead(projectdata,"Iron");
  cost from
 SheetRead(projectdata,"Price_Serving");
   min_serve from
 SheetRead(projectdata,"Min");
   max_serve from
 SheetRead(projectdata,"Max");
    CheckBox from
 SheetRead(projectdata,"CheckBox");
 X = 11;
  A from
  SheetRead(projectdata,"Req_min");
  B from
  SheetRead(projectdata,"req_max");
 Names from 
 SheetRead(projectdata,"Names"); 
  

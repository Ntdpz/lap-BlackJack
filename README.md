# lap-BlackJack
package lap02;
import java.util.Scanner;
import java.util.Random;

public class Blackjack{
    private int[] cardYou = new int[5] ; //จำนวนการ์ด ของคน
    private int[] cardComputer=new int[2];//จำนวนการ์ด ของคอม
    private int sumYou =0; //แต้มทั้งหมดของคน
    private int sumCom =0; //แต้มทั้งหมดของการ์ด
    private String winner; //ผู้ชนะ
    private boolean isEnd; //เช็คเงือนไขการจบเกม
    private int sumNum;
    
    
    Random rand = new Random();
    
    
    public Blackjack() //กำหนดค่าตัวแปร
        {
        //Initialize game data
        
        //Player
        cardYou[0] = rand.nextInt(11)+1;        
        cardYou[1] = rand.nextInt(11)+1; 
        //Dealer
        cardComputer[0]= rand.nextInt(11)+1;
        cardComputer[1]= rand.nextInt(11)+1;
        
        
        //Sum
        //sumYou=cardYou[0]+cardYou[1];
        sumCom=cardComputer[0]+cardComputer[1];

        
        //Check both 11
        if(sumYou==22){
        	cardYou[1]=1;
        	sumYou=12;

        }
        if(sumCom==22){
        
            cardComputer[1] = 1;
            sumCom=12;
        }
    }    
    //นนน ทำเลยยย เป็นกำลังใจให้ นนนสู้ๆนนนสุ้ตาย นนนว้าย
    public void showPlayerCard() //แสดงค่าการ์ดของผู้เล่น
    {
       if(isEnd()==false) 
       {
    	   System.out.print("You : ");
           for(int i=0;i<cardYou.length;i++) {
           	System.out.print(cardYou[i]+" ");
           }
           System.out.println();
           System.out.print("Computer : ");
           				
        } if(isEnd()==true) 
        	{
    	System.out.print("You : ");
        for(int i=0;i<cardYou.length;i++) 
        		{
        	System.out.print(cardYou[i]+" ");	
        		}
        System.out.println();
        System.out.println("Computer : ? ?");
        System.out.println();
        	}
    	}
    
    public void showComputerCard() //แสดงค่าการ์ดของคอม
    {	
    	System.out.print("Computer : ");
    	for(int i=0;i<=1;i++) 
    	{
        	System.out.print(cardComputer[i]+" ");
        }
    	
    }
    
    public void addMorecard() //เพิ่มการ์ดทีละ 1 ใบ ถ้าผู้เล่นต้องการ ใช้เงือนไข y/n  
    {
    	Scanner Sc = new Scanner(System.in);
    	int i = 1;   	
    	while(isEnd()){
    		
    		 System.out.print("Want another card? (y/n)...");
        	 char s = Sc.next().charAt(0); 
    		 i++;
    		 if(i==5) {
    			break;
    		 }
    		 if (s == 'n') {
    			 System.out.print("You : ");
    	           for(int v=0;v<cardYou.length;v++) {
    	           	System.out.print(cardYou[v]+" ");}
    	           System.out.println();
       		isEnd = false ;
       		sumNum=cardYou[0]+cardYou[1]+cardYou[2]+cardYou[3]+cardYou[4];
       		        break;	 
       	 	 }
    		 else if(s == 'y'){
       		 cardYou[i] = rand.nextInt(11)+1;
       		sumNum=cardYou[0]+cardYou[1]+cardYou[2]+cardYou[3]+cardYou[4];
       		 isEnd = true;
       	 	 }
         	showPlayerCard(); 
    	 }
    }	
       
    public void showSumCard() //แสดแต้มรวมทั้งหมด
    {       
    	System.out.println("Sum of Your cards = "+sumNum);
    	System.out.println("Sum of Computer cards = "+sumCom);
    }  
   public boolean isEnd() //เงื่อนไขการจบเกม 
   {
	  
	   if(sumNum>21) {
		   return false;
	   }else if (sumNum>sumCom) {
		   return true;
	   } else {
		   return true;
	   }
   }
	 
   
    
    public void checkWinner()//ประกาศผู้ชนะ
    {
    	if(sumNum>21) {
    		winner ="Computer";
 	   }else if (sumNum>sumCom) {
 		  winner= "You";
 	   } else {
 		  winner="Computer";
 	   }      
        
    }

public String getWinner(){
        return winner;

    }



	public static void main(String[] args) {
Blackjack bj = new Blackjack();                
        
        bj.showPlayerCard();
        bj.addMorecard();
        bj.showComputerCard(); 
        System.out.println();
        bj.showSumCard();
        bj.checkWinner();
        System.out.println("The Winner is " +bj.getWinner());
    }       

}



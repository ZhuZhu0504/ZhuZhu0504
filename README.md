package 程式設計練習;
/*設計一程式，亂數產生四位數的數字，每個位數不重複，千位數不為零。
 讓玩家猜數字。如果相對應的位數猜對的話，記為1A，位數不對但數字相同的話記為1B。*/
import java.util.Scanner;
public class p3 {
	public static void main(String[] args) {
		Scanner input = new Scanner (System.in);
		int a,b,c,d;
		
		a = (int) (Math.random() * 9+1);
		do {b = (int) (Math.random() * 10);}while(a==b);
		do {c = (int) (Math.random() * 10);}while(a==c || b==c);
		do {d = (int) (Math.random() * 10);}while(a==d || b==d || c==d);
		
		int[] list = new int[] {a,b,c,d};
		
		for(int times=1;times>0;times++) {
			System.out.print("請輸入您猜的各位不重複之四位數字");
			String guess=input.next();
			int glist[] = new int [4];//4指的是4個元素
			for(int i=0;i<=3;i++) {
				glist[i]=Character.getNumericValue(guess.charAt(i));}//FOR 把猜的數字各項分開，將char型態轉int，並加入。
			
			int A=0,B=0;//宣告A、B
			for (int i=0;i<=3;i++){
				if (list[i]==glist[i]) {
					A++;}//IF
			}//for A
			if (A==4){
				System.out.println("恭喜答對!答案為"+(a&b&c&d));
				System.out.println("您總共猜了"+times+"次");
						
				break;}//完全猜對結束迴圈
			for (int e=0;e<=3;e++) {
				for (int k=0;k<=3;k++) {
					if (list[e]==glist[k] && list[e]!=glist[e] ) {//因為會把A算進去，所以要把它排除。
						B++;}
				}//B-2for
			}//B-1for
			System.out.println(guess+"為"+A+"A"+B+"B，繼續加油!");
		}//無限FOR
		input.close();
	}
}

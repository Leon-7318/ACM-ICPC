拓扑排序
package 拓扑排序;

import java.util.*;

public class x2 {
	
	static Scanner sc = new Scanner(System.in);
	
	public static void main(String[] args) {
		
		int n = sc.nextInt();
		int[][] a = new int[n+10][n+10];
		int[] in = new int[n+10];
		
		for(int i=1; i<=n; i++) {
			String s = sc.next();
			for(int j=0; j<n; j++) {
				a[i][j+1] = s.charAt(j)-'0';
				if(a[i][j+1]==1) in[j+1]++;
			}
		}
		
		for(int i=1 ;i<=n; i++)
			System.out.print(in[i]+" ");
		System.out.println();
		
		
		Vector<Integer> v = new Vector<Integer>();
		
		do {
			while(!v.isEmpty()) {
				int i = v.remove(0);
				in[i]--;
				for(int j=1; j<=n; j++)
					if(a[i][j] == 1)
						in[j]--;
				System.out.print(i+"->");
			}
			for(int i=1; i<=n; i++)
				if(in[i] == 0)
					v.add(i);
		}while(!v.isEmpty());
	
		System.out.println();
	}

}

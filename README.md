# my-project

import java.util.Scanner;
import java.util.ArrayList;

public class TestApp {
  
  public static void main(String[] args) {
    

    String[] lines = getStdin();
    String [] problem = new String [lines.length] ;
    for (int i = 0, k = lines.length; i < k; i++) {
      String output = String.format("line[%s]: %s", i, lines[i]);
      //System.out.println(output);
      problem[i] = lines[i] ;
    }
  
  String [] nums = problem[0].split(" ") ;
  String Pattern = problem[1] ;
  
  int total = Integer.parseInt(nums[0]) ;
  int shout = Integer.parseInt(nums[1]) ;
  int game = 0 ;

  int [] patternSolve = new int[total] ;

  for ( int i = 0 ; i < total ; i++) {
    if ( Pattern.charAt(i)=='S') {
      patternSolve[i] = 0 ;
    } else {
      patternSolve[i] = 1 ;
      game++ ;
      
    }
  }

  if ( shout!=0 ) {
    for ( int i = 1 ; i < total-1 ; i++) {

      if ( patternSolve[i]==0 && patternSolve[i-1]==0 && patternSolve[i+1]==0){
        patternSolve[i] =  patternSolve[i-1] = patternSolve[i+1] = 1 ;
        game = game +3 ;
        shout-- ;
        }

        if (shout==0){
          break ;
        }
      }
  }

    if ( shout!=0) {

      for ( int i=0 ; i < total-1 ; i++) {

        if ( patternSolve[i]==0 && patternSolve[i+1]== 0) {
          patternSolve[i]= patternSolve[i+1] = 1 ;
          shout-- ;
          game=game +2 ;
        }

        if ( shout== 0) {
          break ;
        }
      }
 }

    if ( shout!=0) {

      for ( int i = 0 ; i < total ; i++) {

        if ( patternSolve[i]==0) {
          patternSolve[i] = 1 ;
          game++ ;
          shout-- ;
        }

        if (shout==0) {
          break ;
        }
      }
    }

  System.out.println(game) ;
   
  }

  private static String[] getStdin() {
    Scanner scanner = new Scanner(System.in);
    ArrayList<String> lines = new ArrayList<>();
    while (scanner.hasNext()) {
      lines.add(scanner.nextLine());
    }
    return lines.toArray(new String[lines.size()]);
  }
}


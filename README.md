# JavaTest

package com.company;

import java.util.*;
import java.io.*;

public class Main {

    private static int MAX = 300;
    private static int ARR_MAX = 50;
    public static void main(String[] args) {
	// write your code here

        People p = new People ();

        String FileName = "exit";
        String userFileName;
        boolean correctFile = false;

        System.out.println("\n");

        while (!correctFile) {
            System.out.println("Please type in the file name\n");

            // create a variable s of type scanner to process input from "System.in"
            Scanner scanSystemIn = new Scanner(System.in);

            // Use the Scanner "s" to get the "next" input from "System.in"
            userFileName = scanSystemIn.next();

            // Display the user input now stored in "userInput"
            System.out.println("\nThe user input: " + userFileName);

            if (userFileName.equalsIgnoreCase(FileName)){

                correctFile = true;
            }
        }


        String GivenName[] = new String [ARR_MAX];
         String FamilyName[] = new String [ARR_MAX];
         String Gender[] = new String [ARR_MAX];


        // ---------------------------------------------
        // This is where we "try" to process the file
        //


        try {
            // --------------------------------
            // create file, and scanner objects

            //

            File userFile = new File(FileName + ".txt");
            Scanner scanUserFile = new Scanner(userFile);

            // ---------------------------------------------
            // Reads in values from the file in a while loop into three different string arrays

             int i = 0;
            while (i < ARR_MAX) {


                    // ---------------------------------------------
                    // The scanner checks if there is another integer and prints it
                    // if there is
                    //

                    if (scanUserFile.hasNext()) {

                        GivenName[i] = scanUserFile.next();
                        FamilyName[i] = scanUserFile.next();
                        Gender[i] = scanUserFile.next();

                        i++;



                    } else {

                        // ---------------------------------------------
                        // The scanner detected no other integers
                        // - closes the scanner for the file
                        // - breaks out of the for loop
                        //
                        System.out.print("\n\nDataFileFILE has been completely READ");
                        scanUserFile.close();

                        // A break statement allows us to exit the loop before we have reach the end
                        break;
                    }


            }



        System.out.println("\n");

        // ---------------------------------------------
        // If the file cannot be found then an exception (error) is generated (thrown) that we have to
        // deal with (catch).
        // - we print "e" the exception, and
        // - show the user where it was using the "exceptions" stack trace information
        //

    } catch (FileNotFoundException e) {
        System.out.println(e);
        e.printStackTrace();
    }



       // Print “Task 1” on a single line on the screen
       // Display all of the data stored in the arrays using a single for loop with 1 persons data on each line.
                //Leave 2 blank lines once this task is completed.


        System.out.println("Task 1 \n");

        for (int i = 0; i < ARR_MAX; i++){
            System.out.println(GivenName[i] + " " + FamilyName[i] + " " + Gender[i] );

        }
        System.out.print("\n\n");

        System.out.println("Task 2a\n");

        String sortedGivenName []= new String [50];

        for (int i=0; i<ARR_MAX; i++) {
                sortedGivenName[i] = GivenName[i];

        }

        String sortedFamilyName []= new String [50];

        for (int i=0; i<ARR_MAX; i++) {

                sortedFamilyName[i] = FamilyName[i];

        }

        String sortedGender []= new String [50];

        for (int i=0; i<ARR_MAX; i++) {
                sortedGender[i] = Gender[i];
        }

        int itemsOnLine =  0;

        p.sortArray(sortedGivenName);
        p.sortArray(sortedFamilyName);
        p.sortArray(sortedGender);


        // use a nested loop

        for (int i=0; i<ARR_MAX; i++) {
            itemsOnLine++;
            System.out.print(sortedGivenName[i] + " ");
            if (itemsOnLine==6){
                System.out.println();
                itemsOnLine =0;
            }
        }

        System.out.print("\n\n");

        System.out.println("Task 2b\n");

      itemsOnLine=0;

      // use a nested loop


         for (int i=0; i<ARR_MAX; i++) {
            itemsOnLine++;
            System.out.print(sortedFamilyName[i] + " ");
            if (itemsOnLine==6){
                System.out.println();
                itemsOnLine =0;
            }
        }



        System.out.print("\n\n");

        System.out.println("Task 2c\n");

        itemsOnLine=0;

        // prints one item per-line using a while loop

        int t = 0;
       while (t < ARR_MAX) {
            itemsOnLine++;
            System.out.print(sortedGender[t] + " ");
            if (itemsOnLine==1){
                System.out.println();
                itemsOnLine =0;
            }
            t++;
        }



        System.out.print("\n\nTask 3\n\n");
        // Create an array of objects to store the People data named peopleData,
        // and using a while loop store all of the original data in the arrays (givenNames, familyNames, gender)
        // into this new array of objects.
        //Display all of the data stored in the peopleData (given name, family name, gender),
        // one person on each new line, using a while loop


       String peopleData [][] = new String [MAX][3];

       for (int i = 0; i < MAX; i ++){
          for (int j = 0; j < 3; j++){
               peopleData [i][j] = "Invalid";
           }
       }

       int count = 0;

       while (count < ARR_MAX){

           peopleData[count][0] = GivenName[count];
           peopleData[count][1] = FamilyName[count];
           peopleData[count][2] = Gender[count];

           System.out.println(peopleData[count][0] + ", " + peopleData[count][1] + ", " + peopleData[count][2] );

           count ++;

       }







    }// end main method
}// end main class

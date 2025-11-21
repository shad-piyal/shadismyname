# shadismyname
i dont know
//File Name EmployeeManager.java
import java.io.*;
import java.util.*;

public class EmployeeManager 
{
    public static void main(String[] args)
     {
      

        

        // Check arguments

if (args.length == 0) 
    {
        System.out.println("No arguments provided.");
        return;
    }

if (args[0].equals("l")) 
    {
        System.out.println("Loading data ...");

    /*  ..................................
        ---if the arguments are valid then---
        .................................. 
    */


        try 
            {
                BufferedReader readintxt = new BufferedReader(
                    new InputStreamReader(
                    new FileInputStream("employees.txt")));
                String linereader = readintxt.readLine();
                String e[] = linereader.split(",");

                for (String emp : e) 
                {
                    System.out.println(emp);
                }
            } 
        catch (Exception e) 
        {
            System.out.println(e);
        }
            System.out.println("Data Loaded.");
    } 

     /*  ..................................
        ---if the arguments pass "s" then---
        .................................. 
    */


else if (args[0].equals("s"))
    {
        System.out.println("Loading data ...");

        try 
        {
            BufferedReader readintxt = new BufferedReader(new InputStreamReader(new FileInputStream("employees.txt")));
            String linereader = readintxt.readLine();
            System.out.println(linereader);
            String e[] = linereader.split(",");

            Random rand = new Random();
            int idx = rand.nextInt(e.length);
            System.out.println(e[idx]);
        } 
        catch (Exception e) 
        {
            System.out.println(e);
        }
            System.out.println("Data Loaded.");
    }

    /*  ..................................
        ---if the arguments pass "+" then---
        .................................. 
    */

else if (args[0].contains("+")) 
    {
        System.out.println("Loading data ...");

    try 
    {
        BufferedWriter writeincode = new BufferedWriter(new FileWriter("employees.txt", true));
        String subStr_n = args[0].substring(1);
        writeincode.write(", " + subStr_n);
        writeincode.close();
    } 
    catch (Exception e) 
    {
        System.out.println(e);
    }
        System.out.println("Data Loaded.");
    } 

    /*  ..................................
        ---if the arguments pass "?" then---
        .................................. 
    */

else if (args[0].contains("?")) 
    {
        System.out.println("Loading data ...");

        try 
        {
            BufferedReader readintxt = new BufferedReader(new InputStreamReader(new FileInputStream("employees.txt")));
            String linereader;
            boolean found = false;
            String subStr_s = args[0].substring(1);
        
            while ((linereader = readintxt.readLine()) != null && !found)
            {
                String e[] = linereader.split(",");
                for (int i = 0; i < e.length && !found; i++) 
                {
                    if (e[i].equals(subStr_s)) 
                    {
                        System.out.println("Employee found!");
                        found = true;
                    }
                }
            }
        } 
        catch (Exception e) 
        {
            System.out.println(e);
        }
        
        System.out.println("Data Loaded.");
    } 
    
    /*  ..................................
        ---if the arguments pass "c" then---
        .................................. 
    */

else if (args[0].contains("c")) 
    {
        System.out.println("Loading data ...");

    try 
    {
        BufferedReader reader = new BufferedReader(new FileReader("employees.txt"));
        String line = reader.readLine();

        int count = 0;

        if (line != null && !line.isBlank()) 
            {
            count = line.trim().split("\\s+").length;
            }

        System.out.println(count + " word(s) found");

    
    } 
    catch (Exception e) 
    {
        System.out.println(e);
    }
        System.out.println("Data Loaded.");
    } 
else if (args[0].contains("u")) 
    {
        System.out.println("Loading data ...");

    try 
    {
            BufferedReader readintxt = new BufferedReader(new InputStreamReader(new FileInputStream("employees.txt")));
            String linereader = readintxt.readLine();
            String e[] = linereader.split(",");
            String subStr_n = args[0].substring(1);

            for (int i = 0; i < e.length; i++) 
                {
                    if (e[i].equals(subStr_n)) 
                        {
                            e[i] = "Updated";
                        }
                }
            BufferedWriter writeincode = new BufferedWriter(new FileWriter("employees.txt"));
                writeincode.write(String.join(",", e));
                writeincode.close();
    } 
    catch (Exception e) 
    {
        System.out.println(e);
    }
        System.out.println("Data Updated.");
    }   

    /*  ..................................
        ---if the arguments pass "d" then---
        .................................. 
    */


else if (args[0].contains("d")) 
    {
        System.out.println("Loading data ...");

    try    
    {
        BufferedReader readintxt = new BufferedReader(new InputStreamReader(new FileInputStream("employees.txt")));
        String linereader = readintxt.readLine();
        String e[] = linereader.split(",");
        String subStr_n = args[0].substring(1);
        List<String> list = new ArrayList<>(Arrays.asList(e));
        list.remove(subStr_n);
        BufferedWriter writeincode = new BufferedWriter(new FileWriter("employees.txt"));
        writeincode.write(String.join(",", list));
        writeincode.close();
    } 
    catch (Exception e) 
    {
        System.out.println(e);
    }
        System.out.println("Data Deleted.");
    }

    }
}

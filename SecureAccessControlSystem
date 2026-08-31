import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class SecureAccessControlSystem
{
    public static String userRole = "none";
    public static void main(String[] args)
    {
        //prompt user for username and password
        Scanner input = new Scanner(System.in);
        System.out.println("Enter username:");
        String inputUsername = input.nextLine();
        System.out.println("Enter password:");
        String inputPassword = input.nextLine();
        //checks if the account is real
        if (checkLogin(inputUsername, inputPassword) == true) {
            System.out.println("LOGIN SUCCESSFUL");
        } else {
            System.out.println("LOGIN FAILED"); 
        }
        //tester
        System.out.println(userRole);
    }
    
    public static boolean checkLogin(String user, String pass) { //checks if a username and password match
        File file = new File("users.txt");
        try {
            Scanner fileReader = new Scanner(file);
            while (fileReader.hasNextLine()) {
                //parses username, password, and role per line of users.txt
                String line = fileReader.nextLine();
                String[] data = line.split(",");
                String username = data[0];
                String password = data[1];
                String role = data[2];
                //checks if this username + password exists
                if (user.equals(username) && pass.equals(password)) {
                    //if they match, take user role and confirm the login
                    userRole = role;
                    fileReader.close();
                    return true;
                }
            } //if none match, the login fails
            fileReader.close();
            return false;
        }
        catch (FileNotFoundException e) { //stops if the file is missing
            System.out.println("File Not Found.");
            return false;
        }
    }
    
    public static void displayUsers() { //displays the entire contents of users.txt; currently unused
        File file = new File("users.txt");
        try {
            Scanner fileReader = new Scanner(file);
            while (fileReader.hasNextLine()) {
                //prints each line of users.txt
                String line = fileReader.nextLine();
                System.out.println(line);
            }
            fileReader.close();
        }
        catch (FileNotFoundException e) { //stops if the file if missing
            System.out.println("File Not Found.");
        }
    }
}

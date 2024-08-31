# Insert_Operation_JDBC

package in.sp.test;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class CRUD_Operations {
    public static void main(String[] args) {

        try {
            Class.forName("com.mysql.cj.jdbc.Driver");

        } catch ( ClassNotFoundException e){
            e.printStackTrace();
        }

        String url = "jdbc:mysql://127.0.0.1:3306/crud_demo";
        String username = "root";
        String password = "Jordan@22@sql";
        String query = "insert into crud values (?, ?, ?, ?)";

        int id = 102;
        String name = "Ram";
        int age = 22;
        String gender = "male";
        try {
            Connection connection = DriverManager.getConnection(url, username, password);
            PreparedStatement preparedStatement = connection.prepareStatement(query);

            preparedStatement.setInt(1, id);
            preparedStatement.setString(2, name);
            preparedStatement.setInt(3, age);
            preparedStatement.setString(4, gender);

            int i = preparedStatement.executeUpdate();
            if (i>0){
                System.out.println("Success.");
            } else {
                System.out.println("Failed.");
            }


        } catch (SQLException e){
            e.printStackTrace();
        }
    }
}

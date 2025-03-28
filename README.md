// Source code is decompiled from a .class file using FernFlower decompiler.
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class EstablishConnection {
   public EstablishConnection() {
   }

   public static void main(String[] var0) {
      String var1 = "jdbc:mysql://localhost:3306/demo";
      String var2 = "root";
      String var3 = "Kalonia@1234";

      try {
         Class.forName("com.mysql.cj.jdbc.Driver");
         Connection var4 = DriverManager.getConnection(var1, var2, var3);

         try {
            System.out.println(" Connected to MySQL successfully!");
         } catch (Throwable var8) {
            if (var4 != null) {
               try {
                  var4.close();
               } catch (Throwable var7) {
                  var8.addSuppressed(var7);
               }
            }

            throw var8;
         }

         if (var4 != null) {
            var4.close();
         }
      } catch (ClassNotFoundException var9) {
         System.out.println(" MySQL Driver not found! Add JDBC Jar.");
      } catch (SQLException var10) {
         System.out.println("Connection failed! Check database settings.");
      }

   }
}

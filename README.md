 
 ConnectionBean is a connect for jdbc odbc java  client driver information for the railway Department
 
 # MATINpackage classes.rail;
import java.sql.*;

public class ConnectionBean
{
private Connection connection;
private Statement statement;
private static final String driver="org.apache.derby.jdbc.ClientDriver";
private static final String dbURL="jdbc:derby://localhost:1527/RailWay Information";
private static final String login="matin999";
private static final String password="matin999";


public ConnectionBean()
{

try
{
	Class.forName(driver);
	connection=DriverManager.getConnection(dbURL,login,password);
	statement=connection.createStatement();

}
catch (ClassNotFoundException e)
{
	System.err.println("ConnectionBean: driver unavailable");
	connection = null;
}
catch (SQLException e)
{
	System.err.println("ConnectionBean: driver not loaded");
	connection = null;
}



}
public Connection getConnection()
{
	return connection;
}




public ResultSet executeQuery(String sql) throws SQLException
{
	return statement.executeQuery(sql);
}

public int executeUpdate(String sql) throws SQLException
{
	return statement.executeUpdate(sql);
}
public boolean execute(String sql) throws SQLException
{
         return statement.execute(sql);
}

    @Override
protected void finalize()
{
try
{
	connection.close();
}
catch (SQLException e)
{
}
}
}

0# java


<!DOCTYPE html>
<html>
<head>
  <title>Login Page</title>
</head>
<body>
  <h2>Login</h2>
  <form action="/login" method="post">
    <label>Username:</label><br>
    <input type="text" name="username" required><br><br>
    
    <label>Password:</label><br>
    <input type="password" name="password" required><br><br>
    
    <input type="submit" value="Login">
  </form>
</body>
</html>
package com.example.EXP8.ProblemA;

import java.io.*;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.*;

@WebServlet("/login")
public class LoginServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws IOException {
        String user = request.getParameter("username");
        String pass = request.getParameter("password");

        response.setContentType("text/html");
        PrintWriter out = response.getWriter();

        if ("admin".equals(user) && "password".equals(pass)) {
            out.println("<html><body>");
            out.println("<h2>Welcome, " + user + "!</h2>");
            out.println("<p>Login successful.</p>");
            out.println("</body></html>");
        } else {
            out.println("<html><body>");
            out.println("<h2>Login Failed</h2>");
            out.println("<p>Invalid username or password. <a href='login.html'>Try again</a>.</p>");
            out.println("</body></html>");
        }
    }
}

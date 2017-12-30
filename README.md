# Clock

    package zegarek;

    import javax.swing.*;
    import java.awt.*;
    import java.awt.event.*;
    import java.util.Calendar;
    import java.util.GregorianCalendar;

    public class Main extends JFrame 
    {

    public Main()
    {
        super("Zegarek");
        this.setBounds(300, 300, 200, 30);
        initComponents();
        this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    }
    
    JPanel panel = new JPanel();
    JLabel etykieta = new JLabel("Czas: ");
    JLabel czas = new JLabel(pobierzCzas());
    static int i = 1;
    
    public void initComponents()
    {
        panel.add(etykieta);
        panel.add(czas);
        
        ActionListener stoper = new Zegar();
        Timer zegar = new Timer(1000, stoper);
        zegar.start();
                
        this.getContentPane().add(panel);
        
    }
    
    private class Zegar implements ActionListener
    {
        @Override
        public void actionPerformed(ActionEvent e) 
        {
          czas.setText(pobierzCzas());
        }   
    }
 
    public String pobierzCzas()
    {
        GregorianCalendar kalendarzyk = new GregorianCalendar();
        String h = "" + kalendarzyk.get(Calendar.HOUR_OF_DAY);
        String m = "" + kalendarzyk.get(Calendar.MINUTE);
        String s = "" + kalendarzyk.get(Calendar.SECOND);

            if (Integer.parseInt(h) < 10) h = "0" + h;
            if (Integer.parseInt(m) < 10) m = "0" + m;
            if (Integer.parseInt(s) < 10) s = "0" + s;

        return h + " : " + m + " : " + s;
    }
    
    public static void main(String[] args) {
        
        new Main().setVisible(true);
        
    }
    
}

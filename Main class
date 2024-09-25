Main class

//Name: Deepansh Thakur
//Game & Theme: Wordle - Attack On Titan (Anime) Themed
//Date: June 18, 2024

//libraries
package Sound;
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class Wordle extends JPanel implements ActionListener
{
	//For screens
	Panel p_card;
	Panel card1, card2, card3, card4;
	CardLayout cdLayout = new CardLayout ();

	//the answer
	Word secret = new Word ();
	JButton ans = new JButton ("");
	int greenLetters = 0;
	int hintsGiven = 0;

	//Game screen's grid
	int row = 6;
	int col = 5;
	int currentRow = 0;
	int currentCol = 0;

	JTextField a[] = new JTextField [row * col];
	String dictionary[] = new String [5757];

	//game screen
	JButton pics[] = new JButton [row * col];
	int sqDimension = 50;
	JButton check, hint;

	//Formatting
	Color backgroundColour = new Color (0, 0, 0);
	Color buttonColour = new Color (0, 74, 173);
	Color buttonColour2 = new Color (56, 118, 29);
	Color buttonText2 = new Color (191, 0 ,0);
	Color KeyColour = new Color (14, 150, 222);
	Color buttonText = new Color (0, 191, 99);
	Color titleColour = new Color (0, 191, 99);
	Font titleFont = new Font ("", Font.BOLD, 30);
	Font promptFont = new Font ("Times New Roman", Font.PLAIN, 20);
	Dimension boardSquare = new Dimension (98, 98);


	public Wordle ()
	{ //setting up screens
		p_card = new Panel ();
		p_card.setLayout (cdLayout);
		opening ();
		instructions ();
		gameScreen ();

		//MUSIC FROM MUSIC CLASS
		String filepath = "themeMusic.wav";
		Sound soundObject = new Sound (); //referencing the class
		soundObject.playMusic (filepath); //referencing the method. passing the file path

		setLayout (new BorderLayout ());
		add ("Center", p_card);
	}

	public void opening ()
	{
		card1 = new Panel ();
		card1.setBackground (backgroundColour);
		JButton opening = new JButton (createImageIcon ("opening.gif"));
		buttons (opening, "next", 400, 570, null, null);
		card1.add (opening);
		p_card.add ("1", card1);
	}

	public void instructions () //game manual screen
	{
		card2 = new Panel ();
		card2.setBackground (backgroundColour);

		JLabel title = new JLabel (createImageIcon ("title.png")); //screen title
		title.setPreferredSize(new Dimension (750, 90));

		JButton skinny2 = new JButton (createImageIcon ("skinny.png"));	
		buttons (skinny2, "s", 400, 20, buttonColour, null);

		JButton skinny = new JButton (createImageIcon ("skinny.png"));	
		buttons (skinny, "s", 400, 20, buttonColour, null);

		Panel playp = new Panel (); 
		JButton play = new JButton (createImageIcon ("b1.png"));	//play button
		buttons (play, "play", 400, 80, buttonColour, null);
		playp.add (play); 

		Panel ins = new Panel ();
		JButton how = new JButton (createImageIcon ("b2.png"));	//instructions screen
		buttons (how, "how", 400, 80, buttonColour, null);
		ins.add (how);

		Panel p3 = new Panel ();
		JButton back = new JButton (createImageIcon ("b3.png"));	//to go back
		buttons (back, "back", 400, 80, buttonColour, null);
		p3.add (back);

		Panel p4 = new Panel ();
		JButton creator = new JButton (createImageIcon ("b4.png")); //to see creator
		buttons (creator, "creator", 400, 80, buttonColour, null);
		p4.add (creator);

		card2.add (skinny2);
		card2.add (title);
		card2.add (skinny);
		card2.add (playp);
		card2.add (ins);
		card2.add (p3);
		card2.add (p4);

		p_card.add ("2", card2);
	}

	public void gameScreen ()
	{
		card4 = new Panel ();
		card4.setBackground (backgroundColour);

		JLabel title = new JLabel (createImageIcon ("Wordle.png"));

		Panel grid = new Panel (new GridLayout (row, col));
		int m = 0;
		for (int i = 0 ; i < row ; i++)
		{
			for (int j = 0 ; j < col ; j++)
			{
				a [m] = new JTextField (2);
				a [m].setFont (new Font ("Times New Roman", Font.PLAIN, 35));
				a [m].setForeground (new Color (205, 22, 22));
				a [m].setHorizontalAlignment (0);
				a [m].setPreferredSize (new Dimension (sqDimension, sqDimension));
				grid.add (a [m]);
				m++;
			}
		}
		add (grid);

		Panel p3 = new Panel ();
		JButton reset = new JButton ("Reset");
		buttons (reset, "reset", 100, 30, buttonColour, null);
		p3.add (reset);

		JButton instruct = new JButton ("Instructions");
		buttons (instruct, "ins", 120, 30, buttonColour, null);
		p3.add (instruct);

		JButton back = new JButton ("Back");
		buttons (back, "back2", 120, 30, buttonColour, null);
		p3.add (back);

		Panel p4 = new Panel ();
		hint = new JButton ("Hint");
		buttons (hint, "hint", 150, 30, buttonColour, null);
		hint.setForeground (buttonText2);
		JButton check = new JButton ("Check"); 
		buttons (check, "check", 150, 30, buttonColour, null);
		check.setForeground (buttonText2);
		p4.add (check);
		p4.add (hint);

		JButton skinny2 = new JButton (createImageIcon ("skinny.png"));	
		buttons (skinny2, "s", 400, 20, buttonColour, null);
		JButton skinny = new JButton (createImageIcon ("skinny.png"));	
		buttons (skinny, "s", 400, 20, buttonColour, null);

		card4.add (title);
		card4.add (skinny2);
		card4.add (grid);
		card4.add (skinny);
		card4.add (p4);
		card4.add (p3);

		p_card.add ("4", card4);
	}

	public void labels (JLabel a, int x, int y, Color h, Font f)  //labels method to shorten code. gets rid of repeated code.
	{
		a.setPreferredSize (new Dimension (x, y));
		a.setForeground (h);
		a.setFont (f);
	}

	public void buttons (JButton b, String actionCommand, int x, int y, Color c, String setBorder)  //buttons method to shorten code. gets rid of constant repeated code.
	{
		b.addActionListener (this);
		b.setActionCommand (actionCommand);
		b.setPreferredSize (new Dimension (x, y));
		b.setBackground (c);
		//	b.setForeground (buttonText);
		b.setBorder (null);
	}

	public void readIn() 
	{
		try (BufferedReader br = new BufferedReader(new FileReader("dictionary.txt"))) {
			String line;
			int i = 0;
			while ((line = br.readLine()) != null)	{
				dictionary[i++] = line.trim();
			}
		} catch (IOException e) {
			e.printStackTrace();
		}
	}

	public boolean BinarySearch (String word)
	{
		int left = 0;
		int right = dictionary.length - 1;
		while (left <= right)
		{
			int mid = left + (right - left) / 2;
			if (dictionary [mid] == null)
			{
				return false;
			}
			if (dictionary [mid].compareTo (word) == 0)
			{
				return true;
			}
			if (dictionary [mid].compareTo (word) < 0)
			{
				left = mid + 1;
			}
			else
			{
				right = mid - 1;
			}
		}
		return false;
	}

	public void markRow ()
	{//mark the letters grey, yellow or green
		boolean check = false;
		greenLetters =0;
		for (int i = 0; i < col; i++)
		{
			String lower = a [currentRow * col + i].getText();
			char c = lower.toLowerCase ().charAt (0);
			a [currentRow * col + i].setForeground (Color.white);
			if (secret.correct (c, i)) //green
				a [currentRow * col + i].setBackground (new Color (107, 170, 100)); 
			else if (secret.contains (c)) //yellow
				a [currentRow * col + i].setBackground (new Color (201, 181, 88)); 
			else //grey
				a [currentRow * col + i].setBackground (new Color (120, 124, 126));
		}
		//move to the next row
		currentRow++;

		if (check == true) {
			currentRow++; //move to the next row if there are letters
		}
		if (currentRow == row) { //if the player used all guesses, end the game
			sixthrow();
		} else if (greenLetters == 5) { // If all letters in the row are correct, player wins
			JOptionPane.showMessageDialog(null, "YOU GOT IT! THE WORD WAS " + secret.getWord(), "WINNER!", JOptionPane.INFORMATION_MESSAGE);
			sixthrow();
		}
	}

	public void reset ()
	{
		for (int i = 0 ; i < a.length ; i++)
		{
			a[i].setBackground (Color.white);
			a[i].setText ("");
			a[i].setFont(new Font ("Times New Roman", Font.PLAIN, 35));
			a[i].setForeground(new Color (205, 22, 22));
		}
		hintsGiven =0;
		currentRow = 0;
		currentCol = 0; 
		secret.getNewWord ();
		hint.setEnabled(true);
		JOptionPane.showMessageDialog (null, "There is now a new word you must guess. Say goodbye to the old one.", "New Word!", JOptionPane.INFORMATION_MESSAGE);

	}

	public void sixthrow() //when the player gets to the last row and runs out of guesses
	{
		boolean correct = true;
		currentRow--;

		for (int i = 0; i < col; i++) {
			int index = currentRow * col + i; //gets the index
			String lower = a[index].getText().toLowerCase();
			char c = lower.charAt(0);
			if (!secret.correct(c, i)) { //if the position and letter don't match
				correct = false;
				break;
			}
		}
		if (!correct) {
			JOptionPane.showMessageDialog(null, "Tough, you didn't get it. The word was " + secret.getWord(), "How sad!", JOptionPane.INFORMATION_MESSAGE);
		} else {
			JOptionPane.showMessageDialog(null, "Wow, you got it! The word was " + secret.getWord(), "Amazing!", JOptionPane.INFORMATION_MESSAGE);
		}

		String[] options = {"Back to game", "Quit", "New Game"};
		Object selectedOption = JOptionPane.showInputDialog(null, "What would you like to do next?", "Where to?", JOptionPane.INFORMATION_MESSAGE, null, options, options[0]);

		if (selectedOption == null) { //cancel
			return; //returns to program
		} else if (selectedOption.equals("Back to game")) {
			cdLayout.show(p_card, "4"); //goes to game screen again
		} else if (selectedOption.equals("Quit")) {
			System.exit(0); //exits the program
		} else if (selectedOption.equals("New Game")) { //goes back to game screen and resets the game
			cdLayout.show(p_card, "4");
			reset();
		}
	}

	public void check () {
		String currentWord = "";
		for (int i = 0; i < col; i++) 
		{
			String lower = a[currentRow * col + i].getText();
			char c = lower.toUpperCase().charAt(0);
			currentWord += c;
		}
		if (secret.getWord().equals(currentWord)) 
		{
			greenLetters = 5;
			JOptionPane.showMessageDialog (null, "You got it! The word was " + secret.getWord (), "Amazing!", JOptionPane.INFORMATION_MESSAGE);
			markRow ();
			sixthrow();
		}
		else {
			JOptionPane.showMessageDialog (null, "Keep trying.", null, JOptionPane.INFORMATION_MESSAGE);
			markRow();
		}
	}

	public void actionPerformed (ActionEvent e)
	{
		if (e.getActionCommand ().equals ("next"))
			cdLayout.show (p_card, "2");
		else if (e.getActionCommand ().equals ("s3"))
			cdLayout.show (p_card, "3");
		else if (e.getActionCommand ().equals ("s4"))
			cdLayout.show (p_card, "4");

		else if(e.getActionCommand ().equals ("play")) {
			cdLayout.show(p_card, "4");
		}
		else if (e.getActionCommand ().equals ("creator"))
			JOptionPane.showMessageDialog (null, createImageIcon ("creator.png"), "Creator", JOptionPane.INFORMATION_MESSAGE);
		else if (e.getActionCommand ().equals ("how"))
			JOptionPane.showMessageDialog (null, createImageIcon ("instructions.png"), "Instructions", JOptionPane.INFORMATION_MESSAGE);
		else if (e.getActionCommand ().equals ("ins"))
			JOptionPane.showMessageDialog (null, createImageIcon ("instructions.png"), "Instructions", JOptionPane.INFORMATION_MESSAGE);
		else if (e.getActionCommand ().equals ("back"))
			cdLayout.show(p_card, "1");
		else if (e.getActionCommand ().equals ("back2")){
			cdLayout.show (p_card, "2");
		}
		else if (e.getActionCommand ().equals ("reset")){
			reset ();
		}
		else if (e.getActionCommand ().equals ("hint")){
			if (hintsGiven == 0) {
				hintsGiven++;
				JOptionPane.showMessageDialog (null, "The first letter of the secret word is " + secret.hint (), "Hint " + hintsGiven, JOptionPane.INFORMATION_MESSAGE);
			}
			else if (hintsGiven == 1) {
				hintsGiven++;
				JOptionPane.showMessageDialog (null, "The last letter of the sceret word is " + secret.hint2 (), "Hint " + hintsGiven, JOptionPane.INFORMATION_MESSAGE);

			}
			else {
				JOptionPane.showMessageDialog (null, "You have used " + hintsGiven + " hints already. No more hints remaining.", "Out of hints", JOptionPane.INFORMATION_MESSAGE);
				hint.setEnabled(false);
			}
		}

		else if (e.getActionCommand ().equals ("check")) 
			check ();
	}

	protected static ImageIcon createImageIcon (String path)
	{
		java.net.URL imgURL = Wordle.class.getResource (path);
		if (imgURL != null)
			return new ImageIcon (imgURL);
		else
			return null;
	}

	public static void main (String[] args)
	{
		JFrame.setDefaultLookAndFeelDecorated (true);
		JFrame frame = new JFrame ("Wordle");
		frame.setDefaultCloseOperation (JFrame.EXIT_ON_CLOSE);
		JComponent newContentPane = new Wordle ();
		newContentPane.setOpaque (true);
		frame.setContentPane (newContentPane);
		frame.setSize (400, 600);
		frame.setVisible (true);
	}
}



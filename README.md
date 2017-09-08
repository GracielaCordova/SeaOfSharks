# SeaOfSharks
Its a game where the player needs to pass to other levels.
//https://github.com/GracielaCordova/SeaOfSharks.git
package application;
	
import javafx.application.Application;
import javafx.event.EventHandler;
import javafx.stage.Stage;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.layout.BorderPane;
import javafx.scene.text.Font;
import javafx.scene.text.FontPosture;
import javafx.scene.text.FontWeight;

public class Main extends Application {
	@Override
	public void start(Stage Stage) {
		Group root = new Group();
		Scene scene = new Scene(root,1460,775);

		Image fondo = new Image("PortadaInicio.jpg");
	    ImageView fndo= new ImageView();
		fndo.setImage(fondo);
		fndo.setFitWidth(1390);
		fndo.setFitHeight(730);

		Button botonStart = new Button("START");
		botonStart.setFont(Font.font("verdana",FontWeight.NORMAL, FontPosture.REGULAR,50));
		
		botonStart.setLayoutX(550);
		botonStart.setLayoutY(600);
		botonStart.setOnMouseClicked(new EventHandler<javafx.scene.input.MouseEvent>()
		{
			public void handle(javafx.scene.input.MouseEvent l)
			{
				Escenario escenario = new Escenario();
				escenario.CrearEscenario(Stage);
			}
		}
		);
		root.getChildren().addAll(fndo,botonStart);
		Stage.setScene(scene);
		Stage.show();
	}
	public static void main(String[] args) {
		launch(args);
	}
}

package application;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import javafx.event.EventHandler;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.ComboBox;
import javafx.scene.image.Image;
import javafx.scene.image.ImageView;
import javafx.scene.input.KeyCode;
import javafx.scene.layout.Pane;
import javafx.scene.text.Font;
import javafx.scene.text.FontPosture;
import javafx.scene.text.FontWeight;
import javafx.scene.text.Text;
import javafx.stage.Stage;

public class Escenario {
	Barco P = new Barco();
	double PBX = P.PosicionBarcoX();
	double PBY = P.PosicionBarcoY();
	double PSX = P.PosicionTiburonX();
	double PSY = P.PosicionTiburonY();
	Pane root = new Pane();

	public void CrearEscenario(Stage stage2)
	{
		Pane root = new Pane();
		Scene scene = new Scene(root,1390,7300);
		
		Image fondo = new Image("Mar.gif");
	    ImageView fndo= new ImageView();
	    fndo.setImage(fondo);
	    fndo.setFitWidth(1390);
	    fndo.setFitHeight(900);
	   
	    Image shark=new Image("tiburon.png");
	    ImageView shrk=new ImageView();
		shrk.setImage(shark);
		shrk.setFitWidth(150);
		shrk.setFitHeight(0);
		shrk.setTranslateX(PSX);
		shrk.setTranslateY(PSY);
	    
	    Image boat=new Image("Barco.gif");
		ImageView bt = new ImageView();
		bt.setImage(boat);
		bt.setFitWidth(100);
		bt.setFitHeight(140);
		bt.setTranslateX(PBX);
		bt.setTranslateY(PBY);
		
		scene.setOnKeyPressed((event)-> {
            if (event.getCode() == KeyCode.RIGHT) {
                if(PBX<=630 ) {
                System.out.println("Derecha");
                PBX=PBX+10;
                bt.setTranslateX(PBX);}
            }
            if (event.getCode() == KeyCode.LEFT) {
            	System.out.println("Izquierda");
                if (PBX>= 10) {
                PBX=PBX-10;
                bt.setTranslateX(PBX);
                }
            }
            if (event.getCode() == KeyCode.UP) {
                if((PBY)>=155) {	
                PBY=PBY-100;
                bt.setTranslateY(PBY);}
            }
            if (event.getCode() == KeyCode.DOWN) {
            	System.out.println("Abajo");
                if((PBY)<=580) {
                PBY=PBY+100;
                bt.setTranslateY(PBY);}
            }
            root.getChildren().addAll(bt);
		});
		Button botonSalir = new Button("SALIR");
		botonSalir.setFont(Font.font("verdana",FontWeight.NORMAL, FontPosture.REGULAR,20));
		botonSalir.setLayoutX(1250);
		botonSalir.setLayoutY(20);
		botonSalir.setOnMouseClicked(new EventHandler<javafx.scene.input.MouseEvent>()
		{
			public void handle(javafx.scene.input.MouseEvent l)
			{
			System.exit(0);
			}
		}
	);
	    root.getChildren().addAll(fndo,shrk,bt,botonSalir);
	    stage2.setScene(scene);
		stage2.show();
	}
}

package application;

public class Barco {
double PBX,PBY,PSX,PSY;
	
	public Barco()
	{
	
	}
	public double PosicionBarcoX()
	{
		PBX=10;
		return PBX;
	}
	
	public double PosicionBarcoY ()
	{
		PBY =84;
		return PBY;
	}
	public double PosicionTiburonX()
	{
		PSX =730;
		return PSX;
	}
	
	public double PosicionTiburonY ()
	{
		PSY =200;
		return PSY;
	}
}

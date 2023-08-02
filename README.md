# Java-2D-drawing-app
//please help debug this java code for meme

import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.TextField;
import javafx.scene.layout.GridPane;
import javafx.stage.Stage;

public class AdditionApp extends Application {

    public static void main(String[] args) {
        launch(args);
    }

    @Override
    public void start(Stage primaryStage) {
        primaryStage.setTitle("Addition App");

        GridPane grid = new GridPane();
        grid.setPadding(new Insets(10, 10, 10, 10));
        grid.setVgap(5);
        grid.setHgap(5);

        Label firstNumberLabel = new Label("First Number:");
        GridPane.setConstraints(firstNumberLabel, 0, 0);

        TextField firstNumberInput = new TextField();
        GridPane.setConstraints(firstNumberInput, 1, 0);

        Label operatorLabel = new Label("Operator:");
        GridPane.setConstraints(operatorLabel, 0, 1);

        TextField operatorInput = new TextField();
        GridPane.setConstraints(operatorInput, 1, 1);

        Label secondNumberLabel = new Label("Second Number:");
        GridPane.setConstraints(secondNumberLabel, 0, 2);

        TextField secondNumberInput = new TextField();
        GridPane.setConstraints(secondNumberInput, 1, 2);

        Button addButton = new Button("Add");
        GridPane.setConstraints(addButton, 1, 3);

        Label resultLabel = new Label("Result:");
        GridPane.setConstraints(resultLabel, 0, 4);

        Label resultOutput = new Label();
        GridPane.setConstraints(resultOutput, 1, 4);

        addButton.setOnAction(e -> {
            try {
                double num1 = Double.parseDouble(firstNumberInput.getText());
                double num2 = Double.parseDouble(secondNumberInput.getText());
                String operator = operatorInput.getText();

                if (operator.equals("+")) {
                    double result = num1 + num2;
                    resultOutput.setText(Double.toString(result));
                } else {
                    resultOutput.setText("Invalid operator!");
                }
            } catch (NumberFormatException ex) {
                resultOutput.setText("Invalid input!");
            }
        });

        grid.getChildren().addAll(firstNumberLabel, firstNumberInput, operatorLabel, operatorInput,
                secondNumberLabel, secondNumberInput, addButton, resultLabel, resultOutput);

        Scene scene = new Scene(grid, 300, 200);
        primaryStage.setScene(scene);
        primaryStage.show();
    }
}





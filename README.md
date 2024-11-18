# Online-Quiz-Game
Online quiz games are a fun, interactive, and often educational way to test your knowledge while competing against others. With a wide range of topics and game formats, they provide an engaging experience for casual gamers, trivia enthusiasts, and those looking to improve their knowledge in various fields.
import java.util.Scanner;

class Question {
    String question;
    String[] options;
    char correctAnswer;

    Question(String question, String[] options, char correctAnswer) {
        this.question = question;
        this.options = options;
        this.correctAnswer = correctAnswer;
    }

    void displayQuestion() {
        System.out.println(question);
        for (int i = 0; i < options.length; i++) {
            System.out.println((char) ('A' + i) + ". " + options[i]);
        }
    }

    boolean checkAnswer(char userAnswer) {
        return Character.toUpperCase(userAnswer) == correctAnswer;
    }
}

class QuizGame {
    static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        Question[] questions = {
            new Question("What is the capital of France?", new String[]{"Paris", "London", "Berlin", "Madrid"}, 'A'),
            new Question("Which planet is known as the Red Planet?", new String[]{"Earth", "Mars", "Jupiter", "Saturn"}, 'B'),
            new Question("Who wrote 'Romeo and Juliet'?", new String[]{"William Shakespeare", "Charles Dickens", "Mark Twain", "Jane Austen"}, 'A'),
            new Question("What is the largest ocean on Earth?", new String[]{"Atlantic Ocean", "Indian Ocean", "Pacific Ocean", "Arctic Ocean"}, 'C')
        };

        int score = 0;

        System.out.println("Welcome to the Quiz Game!");
        System.out.println("You will be asked 4 questions. Answer with A, B, C, or D.");
        
        for (Question q : questions) {
            q.displayQuestion();
            System.out.print("Your answer: ");
            char userAnswer = scanner.next().charAt(0);
            
            if (q.checkAnswer(userAnswer)) {
                System.out.println("Correct!");
                score++;
            } else {
                System.out.println("Wrong! The correct answer was " + q.correctAnswer);
            }
            System.out.println();
        }

        System.out.println("You completed the quiz!");
        System.out.println("Your total score: " + score + " out of " + questions.length);
        
        if (score == questions.length) {
            System.out.println("Excellent! You got all questions right!");
        } else if (score >= questions.length / 2) {
            System.out.println("Good job! You got more than half right.");
        } else {
            System.out.println("Better luck next time!");
        }
    }
}

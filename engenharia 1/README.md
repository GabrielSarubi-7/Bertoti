Atividade 1:
What precisely do we mean by software engineering? What distinguishes “software engineering” from “programming” or “computer science”? And why would Google have a unique perspective to add to the corpus of previous software engineering literature written over the past 50 years?
 
The terms “programming” and “software engineering” have been used interchangeably for quite some time in our industry, although each term has a different emphasis and different implications. University students tend to study computer science and get jobs writing code as “programmers.”
 
“Software engineering,” however, sounds more serious, as if it implies the application of some theoretical knowledge to build something real and precise. Mechanical engineers, civil engineers, aeronautical engineers, and those in other engineering disciplines all practice engineering. They all work in the real world and use the application of their theoretical knowledge to create something real. Software engineers also create “something real,” though it is less tangible than the things other engineers create.
 
Unlike those more established engineering professions, current software engineering theory or practice is not nearly as rigorous. Aeronautical engineers must follow rigid guidelines and practices, because errors in their calculations can cause real damage; programming, on the whole, has traditionally not followed such rigorous practices. But, as software becomes more integrated into our lives, we must adopt and rely on more rigorous engineering methods. We hope this book helps others see a path toward more reliable software practices.

Comentario: O texto implica que o termo "Software engineering" ou engenharia de software, tem um tom mais sério e mais ligado ao trabalho do dia a dia, muito mais do que apenas escrever linhas de codigos mas entender e aplicar sua praticidade em tecnologias do mundo real.

Atividade 2:
Programming Over Time
We propose that “software engineering” encompasses not just the act of writing code, but all of the tools and processes an organization uses to build and maintain that code over time. What practices can a software organization introduce that will best keep its code valuable over the long term? How can engineers make a codebase more sustainable and the software engineering discipline itself more rigorous? We don’t have fundamental answers to these questions, but we hope that Google’s collective experience over the past two decades illuminates possible paths toward finding those answers.
 
One key insight we share in this book is that software engineering can be thought of as “programming integrated over time.” What practices can we introduce to our code to make it sustainable—able to react to necessary change—over its life cycle, from conception to introduction to maintenance to deprecation?
 
The book emphasizes three fundamental principles that we feel software organizations should keep in mind when designing, architecting, and writing their code:
 
Time and Change
How code will need to adapt over the length of its life
 
Scale and Growth
How an organization will need to adapt as it evolves
 
Trade-offs and Costs
How an organization makes decisions, based on the lessons of Time and Change and Scale and Growth

Comentario: A engenharia de software está em constante mudança e evolução, com o avanço das tecnologias novas mentalidades e abordagens quanto aos metodos são atualizados e moldados de acordo com o ambiente necessario.

Atividade 3:
Exemplo 1 => a escolha entre linux e windowns na empresa, linux é um sistema operacional que te permite ter mais liberdade, segurança e é gratuito, porém ele é bem menos usados do que o windowns e exige treinamento para atingir eficiencia para a equipe;

Exemplo 2=> Entre Java e Python, Java é mais rapido porém demanda de mais sintaxes e tem como foco a portabilidade para tecnologias variadas enquanto Python é de alto nivel portanto mais perto do programador enquanto é mais lenta;

Exemplo 3=> HD e SSD, HD sendo mais barato porém mais lento e SSD o contrario.

Atividade 4:
O método mvp sugere que a cada entrega feita deve haver um "minimo produto viavel" para ser apresentado ao cliente, visando entregas concisas e indicando a progressão de forma mais clara, uma versão reduzida do produto final que é aprimorada a cada entrega de forma que cada versão seja funcional.



Atividade 5:
===== Livro.java =====
package biblioteca;

public class Livro {

    private String titulo;
    private String isbn;

    public Livro(String titulo, String isbn) {
        this.titulo = titulo;
        this.isbn = isbn;
    }

    public String getTitulo() {
        return titulo;
    }

    public void setTitulo(String titulo) {
        this.titulo = titulo;
    }

    public String getIsbn() {
        return isbn;
    }

    public void setIsbn(String isbn) {
        this.isbn = isbn;
    }
}


===== Biblioteca.java =====
package biblioteca;

import java.util.ArrayList;
import java.util.List;

public class Biblioteca {

    private List<Livro> livros = new ArrayList<>();

    public void addLivro(Livro livro) {
        livros.add(livro);
    }

    public Livro buscarLivroISBN(String isbn) {
        for (Livro livro : livros) {
            if (livro.getIsbn().equals(isbn)) {
                return livro;
            }
        }
        return null;
    }

    public List<Livro> buscarLivroTitulo(String titulo) {
        List<Livro> encontrados = new ArrayList<>();
        for (Livro livro : livros) {
            if (livro.getTitulo().equalsIgnoreCase(titulo)) {
                encontrados.add(livro);
            }
        }
        return encontrados;
    }

    public List<Livro> getLivros() {
        return livros;
    }
}


===== Principal.java =====
package biblioteca;

public class Principal {

    public static void main(String[] args) {
        Biblioteca biblioteca = new Biblioteca();

        biblioteca.addLivro(new Livro("Aventuras de Java", "123456"));
        biblioteca.addLivro(new Livro("Estruturas de Dados", "654321"));
        biblioteca.addLivro(new Livro("Aventuras de Java", "999999"));

        Livro livro1 = biblioteca.buscarLivroISBN("123456");
        System.out.println("Livro encontrado por ISBN: " + livro1.getTitulo());

        System.out.println("Livros com o título 'Aventuras de Java':");
        for (Livro l : biblioteca.buscarLivroTitulo("Aventuras de Java")) {
            System.out.println("- " + l.getTitulo() + " [" + l.getIsbn() + "]");
        }

        System.out.println("\nTodos os livros cadastrados:");
        for (Livro l : biblioteca.getLivros()) {
            System.out.println("- " + l.getTitulo() + " [" + l.getIsbn() + "]");
        }
    }
}



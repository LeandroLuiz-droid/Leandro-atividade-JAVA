# Leandro-atividade-JAVA

interface Desconto {
    void aplicarDesconto(double porcentagem);
}

abstract class Veiculo implements Desconto {
    private String marca, modelo;
    private int ano;
    private double preco;

    public Veiculo(String marca, String modelo, int ano, double preco) {
        this.marca = marca;
        this.modelo = modelo;
        this.ano = ano;
        this.preco = preco;
    }

    public String getMarca() { return marca; }
    public String getModelo() { return modelo; }
    public int getAno() { return ano; }
    public double getPreco() { return preco; }

    public void setPreco(double preco) { this.preco = preco; }

    public void aplicarDesconto(double porcentagem) {
        preco -= preco * (porcentagem / 100);
    }

    public abstract void exibirDetalhes();
}

class Carro extends Veiculo {
    private int portas;

    public Carro(String marca, String modelo, int ano, double preco, int portas) {
        super(marca, modelo, ano, preco);
        this.portas = portas;
    }

    public void exibirDetalhes() {
        System.out.println("Carro: " + getMarca() + " " + getModelo() + " " + getAno() +
                           " | R$" + getPreco() + " | Portas: " + portas);
    }
}

class Moto extends Veiculo {
    private int cilindradas;

    public Moto(String marca, String modelo, int ano, double preco, int cilindradas) {
        super(marca, modelo, ano, preco);
        this.cilindradas = cilindradas;
    }

    public void exibirDetalhes() {
        System.out.println("Moto: " + getMarca() + " " + getModelo() + " " + getAno() +
                           " | R$" + getPreco() + " | Cilindradas: " + cilindradas);
    }
}

public class Main {
    public static void main(String[] args) {
        Carro c = new Carro("Chevrolet", "Onix", 2023, 80000, 4);
        Moto m = new Moto("Yamaha", "MT-03", 2022, 32000, 321);

        c.aplicarDesconto(8);
        m.aplicarDesconto(5);

        c.exibirDetalhes();
        m.exibirDetalhes();
    }
}




# Leandro-atividade-JAVA 2


interface FiguraPlana {
    double calcularArea();
    double calcularPerimetro();
}

interface FiguraEspacial {
    double calcularVolume();
}

abstract class Figura {
    public abstract void exibirDetalhes();
}

class Circulo extends Figura implements FiguraPlana {
    private double r;
    public Circulo(double r) { this.r = r; }

    public double calcularArea() { return Math.PI * r * r; }
    public double calcularPerimetro() { return 2 * Math.PI * r; }

    public void exibirDetalhes() {
        System.out.println("Círculo - Área: " + calcularArea() + " | Perímetro: " + calcularPerimetro());
    }
}

class Retangulo extends Figura implements FiguraPlana {
    private double l, h;
    public Retangulo(double l, double h) { this.l = l; this.h = h; }

    public double calcularArea() { return l * h; }
    public double calcularPerimetro() { return 2 * (l + h); }

    public void exibirDetalhes() {
        System.out.println("Retângulo - Área: " + calcularArea() + " | Perímetro: " + calcularPerimetro());
    }
}

class Triangulo extends Figura implements FiguraPlana {
    private double a, b, c;
    public Triangulo(double a, double b, double c) { this.a = a; this.b = b; this.c = c; }

    public double calcularArea() {
        double s = (a + b + c) / 2;
        return Math.sqrt(s * (s - a) * (s - b) * (s - c));
    }

    public double calcularPerimetro() { return a + b

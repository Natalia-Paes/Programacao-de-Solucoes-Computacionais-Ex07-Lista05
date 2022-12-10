# Programacao-de-Solucoes-Computacionais-Ex07-Lista05
Faça um programa que use a função valorPagamento para determinar o valor a ser pago por uma prestação de uma conta.
import java.util.Scanner;

public class Ex07 {
    public static void main(String[] args) throws Exception {
        int qtdPrestacao = 0;
        double valorTotalDia = 0;
        Scanner sc = new Scanner(System.in);
        while (true) {
            System.out.println("Informe o valor da prestação: ");
            double valorPrestacao = sc.nextDouble();
            if (valorPrestacao == 0) {
                break;
            }
            System.out.println("Informe o número de atraso em dias: ");
            int diasAtrasados = sc.nextInt();

            double valorTotal = valorPagamento(valorPrestacao, diasAtrasados);

            System.out.println("O valor a ser pago será de " + String.format("%.2f", valorTotal));
            System.out.println("                                        ");

            qtdPrestacao++;
            valorTotalDia += valorTotal;
        }

        System.out.println("               Relatório Prestações               ");
        System.out.println("Quantidade de prestações: " + qtdPrestacao);
        System.out.println("Valor total de prestações: R$ " + String.format("%.2f", valorTotalDia));
        System.out.println("                                        ");
        sc.close();

    }

    public static double valorPagamento(double valorPrestacao, double diasAtrasados) {
        double valorAPagar = 0;
        if (diasAtrasados > 0) {
            double percentual = 0.03;
            double juros = 0.001;
            double valorMulta = valorPrestacao + (valorPrestacao * percentual);
            valorAPagar = valorMulta + (valorMulta * juros * diasAtrasados);
        } else {
            return valorPrestacao;
        }
        return valorAPagar;
    }
}

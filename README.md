import java.util.ArrayList;
import java.util.Scanner;

public class CalculadoraOrcamento {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Double> receitas = new ArrayList<>();
        ArrayList<Double> despesas = new ArrayList<>();

        System.out.println("=== Calculadora de Orçamento Pessoal ===");

        // Receitas
        System.out.print("Quantas fontes de receita você tem? ");
        int numReceitas = scanner.nextInt();
        for (int i = 0; i < numReceitas; i++) {
            System.out.print("Digite o valor da receita " + (i + 1) + ": R$ ");
            receitas.add(scanner.nextDouble());
        }

        // Despesas
        System.out.print("\nQuantas despesas você tem? ");
        int numDespesas = scanner.nextInt();
        for (int i = 0; i < numDespesas; i++) {
            System.out.print("Digite o valor da despesa " + (i + 1) + ": R$ ");
            despesas.add(scanner.nextDouble());
        }

        // Cálculo
        double totalReceitas = receitas.stream().mapToDouble(Double::doubleValue).sum();
        double totalDespesas = despesas.stream().mapToDouble(Double::doubleValue).sum();
        double saldoFinal = totalReceitas - totalDespesas;

        // Resultado
        System.out.println("\n=== Resumo Financeiro ===");
        System.out.printf("Total de Receitas: R$ %.2f\n", totalReceitas);
        System.out.printf("Total de Despesas: R$ %.2f\n", totalDespesas);
        System.out.printf("Saldo Final: R$ %.2f\n", saldoFinal);

        if (saldoFinal > 0) {
            System.out.println("Situação: Superávit ✅");
        } else if (saldoFinal < 0) {
            System.out.println("Situação: Déficit ❌");
        } else {
            System.out.println("Situação: Equilíbrio ⚖️");
        }

        scanner.close();
    }
}

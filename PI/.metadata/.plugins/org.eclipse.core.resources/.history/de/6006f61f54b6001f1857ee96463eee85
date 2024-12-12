package Boletim;

import java.io.*;
import java.util.*;

public class Boletim_V3 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner scn = new Scanner(System.in);

		System.out.print("Nome da turma: ");
		String nomeTurma = scn.nextLine();

		System.out.print("Unidade Curricular: ");
		String uCurricular = scn.nextLine();

		System.out.print("Nome do professor: ");
		String nomeProf = scn.nextLine();

		String[] nomesAlunos = new String[5];
		int[][] notasAlunos = new int[5][4];
		int[] faltasAlunos = new int[5];
		double[] mediasFinais = new double[5];

		for (int i = 0; i < 5; i++) {
			System.out.print("\nNome do aluno " + (i + 1) + ": ");
			nomesAlunos[i] = scn.nextLine();

			int somaNotas = 0;
			for (int j = 0; j < 4; j++) {
				while (true) {
					System.out.print("Nota " + (j + 1) + " (0 a 100): ");
					String inputNota = scn.nextLine();
					try {
						int nota = Integer.parseInt(inputNota);
						if (nota >= 0 && nota <= 100) {
							notasAlunos[i][j] = nota;
							somaNotas += nota;
							break;
						} else {
							System.err.println("Nota inválida! A nota deve estar entre 0 e 100.");
						}
					} catch (NumberFormatException e) {
						System.err.println("Entrada inválida! Por favor, insira um número.");
					}
				}
			}

			mediasFinais[i] = somaNotas / 4.0;

			while (true) {
				System.out.print("Faltas (0 a 10): ");
				String inputFaltas = scn.nextLine();
				try {
					int faltas = Integer.parseInt(inputFaltas);
					if (faltas >= 0 && faltas <= 10) {
						faltasAlunos[i] = faltas;
						break;
					} else {
						System.err.println("Número de faltas inválido! O valor deve estar entre 0 e 10.");
					}
				} catch (NumberFormatException e) {
					System.err.println("Entrada inválida! Por favor, insira um número.");
				}
			}
		}

		double somaMediaTurma = 0;
		for (double media : mediasFinais) {
			somaMediaTurma += media;
		}
		double mediaGeralTurma = somaMediaTurma / 5;

		int alunosAcimaMedia = 0;
		int alunosAbaixoMedia = 0;
		int melhorAluno = 0;
		int piorAluno = 0;

		for (int i = 0; i < 5; i++) {
			if (mediasFinais[i] > mediaGeralTurma) {
				alunosAcimaMedia++;
			} else if (mediasFinais[i] < mediaGeralTurma) {
				alunosAbaixoMedia++;
			}
			if (mediasFinais[i] > mediasFinais[melhorAluno]) {
				melhorAluno = i;
			}
			if (mediasFinais[i] < mediasFinais[piorAluno]) {
				piorAluno = i;
			}
		}

		System.out.println("\n======= Boletim Escolar =======");
		System.out.println("Professor: " + nomeProf);
		System.out.println("Unidade Curricular: " + uCurricular);
		System.out.println("Turma: " + nomeTurma);
		for (int i = 0; i < 5; i++) {
			System.out.println("\nAluno: " + nomesAlunos[i]);
			for (int j = 0; j < 4; j++) {
				System.out.println("Nota " + (j + 1) + ": " + notasAlunos[i][j]);
			}
			System.out.println("Faltas: " + faltasAlunos[i]);
			System.out.println("Média Final: " + String.format("%.1f", mediasFinais[i]));
			System.out.println("Situação: " + situacao(mediasFinais[i], faltasAlunos[i]));
		}

		System.out.println("\nMédia geral da turma: " + String.format("%.1f", mediaGeralTurma));
		System.out.println("Alunos acima da média geral: " + alunosAcimaMedia);
		System.out.println("Alunos abaixo da média geral: " + alunosAbaixoMedia);
		System.out.println("Aluno com maior média: " + nomesAlunos[melhorAluno]);
		System.out.println("Aluno com menor média: " + nomesAlunos[piorAluno]);
		System.out.println("Melhor aluno: " + nomesAlunos[melhorAluno] + " com média "
				+ String.format("%.1f", mediasFinais[melhorAluno]));
		

		try (FileWriter writer = new FileWriter("boletimEscolar.txt")) {
			writer.write("====== Boletim Escolar ======\n");
			writer.write("Professor: " + nomeProf + "\n");
			writer.write("Unidade Curricular: " + uCurricular + "\n");
			writer.write("Turma: " + nomeTurma + "\n");
			for (int i = 0; i < 5; i++) {
				writer.write("\nAluno: " + nomesAlunos[i] + "\n");
				for (int j = 0; j < 4; j++) {
					writer.write("Nota " + (j + 1) + ": " + notasAlunos[i][j] + "\n");
				}
				writer.write("Faltas: " + faltasAlunos[i] + "\n");
				writer.write("Média Final: " + String.format("%.1f", mediasFinais[i]) + "\n");
				writer.write("Situação: " + situacaoTxt(mediasFinais[i], faltasAlunos[i]) + "\n");
			}
			writer.write("\nMédia geral da turma: " + String.format("%.1f", mediaGeralTurma) + "\n");
			writer.write("Alunos acima da média geral: " + alunosAcimaMedia + "\n");
			writer.write("Alunos abaixo da média geral: " + alunosAbaixoMedia + "\n");
			writer.write("Aluno com maior média: " + nomesAlunos[melhorAluno] + "\n");
			writer.write("Aluno com menor média: " + nomesAlunos[piorAluno] + "\n");
			writer.write("Melhor aluno: " + nomesAlunos[melhorAluno] + " com média "
					+ String.format("%.1f", mediasFinais[melhorAluno]));

			System.out.println("\nBoletim salvo em boletimEscolar.txt!");
		} catch (IOException e) {
			System.err.println("Erro ao salvar o boletim: " + e.getMessage());
		}

		scn.close();
	}

	public static final String ANSI_RESET = "\u001B[0m";
	public static final String ANSI_RED = "\u001B[31m";
	public static final String ANSI_GREEN = "\u001B[32m";
	public static final String ANSI_YELLOW = "\u001B[33m";

	private static String situacao(double mediaFinal, int faltas) {
		if (mediaFinal >= 70 && faltas < 2) {
			return ANSI_GREEN + "Aprovado" + ANSI_RESET;
		} else if (mediaFinal >= 50 && mediaFinal < 70 && faltas < 5) {
			return ANSI_YELLOW + "Recuperação" + ANSI_RESET;
		} else {
			return ANSI_RED + "Reprovado" + ANSI_RESET;
		}
	}

	private static String situacaoTxt(double mediaFinal, int faltas) {
		if (mediaFinal >= 70 && faltas < 2) {
			return "Aprovado";
		} else if (mediaFinal >= 50 && mediaFinal < 70 && faltas < 5) {
			return "Recuperação";
		} else {
			return "Reprovado";
		}
	}
}
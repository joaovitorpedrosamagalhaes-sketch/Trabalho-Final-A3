ALUNOS : João Vitor Pedrosa Magalhaes, Luiz Guilherme, Caua Furst, Silas Caleb.

CÓDIGO : 
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        ArrayList<Profissional> profissionais = new ArrayList<>();

        double totalFinanceiro = 0;
        int opcao;

        do {

            System.out.println("\n SISTEMA DE SERVIÇOS DOMESTICOS ");
            System.out.println("1 - Cadastrar profissional");
            System.out.println("2 - Consultar profissionais");
            System.out.println("3 - Editar profissional");
            System.out.println("4 - Excluir profissional");
            System.out.println("5 - Contratar serviço");
            System.out.println("6 - Gestao financeira");
            System.out.println("0 - Sair");

            System.out.print("Opçao: ");
            opcao = sc.nextInt();
            sc.nextLine();

            switch (opcao) {

                case 1:

                    System.out.print("Nome: ");
                    String nome = sc.nextLine();

                    System.out.print("Especialidade (Encanador, Eletricista, Empregado): ");
                    String especialidade = sc.nextLine();

                    profissionais.add(new Profissional(nome, especialidade));

                    System.out.println("Profissional cadastrado!");
                    break;

                case 2:

                    if (profissionais.isEmpty()) {
                        System.out.println("Nenhum profissional cadastrado.");
                    } else {

                        for (int i = 0; i < profissionais.size(); i++) {
                            System.out.println("\nCódigo: " + i);
                            System.out.println(profissionais.get(i));
                        }

                    }

                    break;

                case 3:

                    System.out.print("Digite a opç1ao do profissional: ");
                    int editar = sc.nextInt();
                    sc.nextLine();

                    if (editar >= 0 && editar < profissionais.size()) {

                        System.out.print("Novo nome: ");
                        profissionais.get(editar).nome = sc.nextLine();

                        System.out.print("Nova especialidade: ");
                        profissionais.get(editar).especialidade = sc.nextLine();

                        System.out.println("Profissional atualizado!");

                    } else {
                        System.out.println("Codigo invalido.");
                    }

                    break;

                case 4:

                    System.out.print("Digite o codigo do profissional: ");
                    int excluir = sc.nextInt();

                    if (excluir >= 0 && excluir < profissionais.size()) {

                        profissionais.remove(excluir);

                        System.out.println("Profissional removido!");

                    } else {
                        System.out.println("Codigo invalido.");
                    }

                    break;

                case 5:

                    System.out.println("\nEscolha o servico:");
                    System.out.println("1 - Encanamento (R$120)");
                    System.out.println("2 - Servico Eletrico (R$180)");
                    System.out.println("3 - Troca de Chuveiro (R$90)");
                    System.out.println("4 - Arrumar Casa (R$90)");

                    int servico = sc.nextInt();

                    switch (servico) {

                        case 1:
                            totalFinanceiro += 120;
                            System.out.println("Serviço contratado!");
                            break;

                        case 2:
                            totalFinanceiro += 180;
                            System.out.println("Servico contratado!");
                            break;

                        case 3:
                            totalFinanceiro += 90;
                            System.out.println("Servico contratado!");
                            break;
                            
case 4:
                            totalFinanceiro += 90;
                            System.out.println("Servico contratado!");
                            break;
                        default:
                            System.out.println("Servico invalido.");

                    }

                    break;

                case 6:

                    System.out.println("Total arrecadado: R$ " + totalFinanceiro);

                    break;

                case 0:

                    System.out.println("Encerrando sistema...");
                    break;

                default:

                    System.out.println("Opçao invalida.");

            }

        } while (opcao != 0);

        sc.close();

    }

}

class Profissional {

    String nome;
    String especialidade;

    public Profissional(String nome, String especialidade) {
        this.nome = nome;
        this.especialidade = especialidade;
    }

    @Override
    public String toString() {
        return "Nome: " + nome + "\nEspecialidade: " + especialidade;
    }

}

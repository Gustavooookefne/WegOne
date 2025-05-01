# WegOne
beta bese classroom systems development

import java.util.Scanner;
import java.text.Normalizer;

public class SistemaNormal {

    // Função para normalizar texto (remove acentos e coloca em minúsculas)
    public static String normalizar(String texto) {
        return Normalizer.normalize(texto, Normalizer.Form.NFD)
                         .replaceAll("[\\p{InCombiningDiacriticalMarks}]", "")
                         .toLowerCase();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // VARIAVEIS
        String nomeOrientacao;
        int menu;
        String atualizarOrientacao;
        int idioma;
        int i = 10;
        int c = 0;

        // ARRAY
        String tituloDaOrientacao[] = new String[11];
        String tipoDaOrientacao[] = new String[11];

        // Idioma
        do {
            System.out.println("\n════════════════════════════════════════");
            System.out.println("       🌍 Escolha o idioma do sistema           ");
            System.out.println("════════════════════════════════════════");
            System.out.println("  1 - Português");
            System.out.println("  2 - Inglês");
            System.out.println("  3 - Alemão");
            System.out.println("  4 - Espanhol");
            System.out.println("  5 - Francês");
            System.out.println("════════════════════════════════════════");
            System.out.print("Digite sua opção: ");
            idioma = sc.nextInt();

            if (idioma >= 1 && idioma <= 5) {
                c++;
            }
        } while (c == 0);

        // SISTEMA EM PORTUGUÊS:
        if (idioma == 1) {

            // DADOS INICIAIS
            tituloDaOrientacao[0] = "Manual de Operação de Motores";
            tipoDaOrientacao[0] = "Manual de Operação";
            tituloDaOrientacao[1] = "Procedimento de Segurança para Instalação Elétrica";
            tipoDaOrientacao[1] = "Procedimento de Segurança";
            tituloDaOrientacao[2] = "Manutenção de Motores Elétricos";
            tipoDaOrientacao[2] = "Manutenção e Reparos";
            tituloDaOrientacao[3] = "Teste de Diagnóstico de Transformadores";
            tipoDaOrientacao[3] = "Testes e Diagnóstico";
            tituloDaOrientacao[4] = "Manual de Conduta no Setor de Montagem";
            tipoDaOrientacao[4] = "Manual de Conduta e Operações Setoriais";
            tituloDaOrientacao[5] = "Procedimento de Segurança com Risco de Choque Elétrico";
            tipoDaOrientacao[5] = "Procedimento de Segurança";
            tituloDaOrientacao[6] = "Manutenção de Geradores de Energia";
            tipoDaOrientacao[6] = "Manutenção e Reparos";
            tituloDaOrientacao[7] = "Teste de Funcionamento de Equipamentos de Automação";
            tipoDaOrientacao[7] = "Testes e Diagnóstico";
            tituloDaOrientacao[8] = "Manual de Operação de Equipamentos de Soldagem";
            tipoDaOrientacao[8] = "Manual de Operação";
            tituloDaOrientacao[9] = "Procedimento de Segurança no Setor de Montagem";
            tipoDaOrientacao[9] = "Procedimento de Segurança";

            // MENU
            do {
                System.out.println("\n════════════════════════════════════════");
                System.out.println("          📋 MENU PRINCIPAL           ");
                System.out.println("════════════════════════════════════════");
                System.out.println("  1 - 📝 Cadastrar");
                System.out.println("  2 - 🔍 Pesquisar");
                System.out.println("  3 - ✏️ Editar");
                System.out.println("  4 - ❌ Excluir");
                System.out.println("  5 - 📊 Exibir");
                System.out.println("  6 - 🚪 Sair");
                System.out.println("════════════════════════════════════════");
                System.out.print("Selecione uma opção: ");
                menu = sc.nextInt();
                sc.nextLine();

             // 1 CADASTRAR
                if (menu == 1) {
                    if (i >= tituloDaOrientacao.length) {
                        String[] novoTitulo = new String[tituloDaOrientacao.length + 1];
                        String[] novoTipo = new String[tipoDaOrientacao.length + 1];
                        for (int j = 0; j < tituloDaOrientacao.length; j++) {
                            novoTitulo[j] = tituloDaOrientacao[j];
                            novoTipo[j] = tipoDaOrientacao[j];
                        }
                        tituloDaOrientacao = novoTitulo;
                        tipoDaOrientacao = novoTipo;
                    }

                    System.out.println("\n\nEscreva o título da orientação: ");
                    tituloDaOrientacao[i] = sc.nextLine();
                    System.out.println("\nEscreva o Tipo da orientação: ");
                    tipoDaOrientacao[i] = sc.nextLine();
                    i++;

                 // 2 PESQUISAR
                } else if (menu == 2) {
                    System.out.println("\nTipos de Orientações disponíveis...\n");
                    for (int d = 0; d < i; d++) {
                        System.out.println("📂 Tipo da Orientação: " + tipoDaOrientacao[d]);
                    }

                    System.out.println("\n\nPesquise o tipo da orientação: ");
                    String nomeTipo = sc.nextLine();

                    boolean encontrado = false;
                    for (int j = 0; j < i; j++) {
                        if (normalizar(nomeTipo).equals(normalizar(tipoDaOrientacao[j]))) {
                            encontrado = true;
                            break;
                        }
                    }

                    if (!encontrado) {
                        System.out.println("\n❌ Tipo de orientação não encontrado!");
                        return;
                    }

                    System.out.println("\n══════════════════════════════════════════════════════════════════════════");
                    System.out.println("Todos os títulos com o tipo de orientação: " + nomeTipo);
                    System.out.println("══════════════════════════════════════════════════════════════════════════\n");

                    for (int n = 0; n < i; n++) {
                        if (normalizar(tipoDaOrientacao[n]).equals(normalizar(nomeTipo))) {
                            System.out.println("🔖 " + tituloDaOrientacao[n]);
                        }
                    }

                    System.out.println("\n\nSelecione um título da orientação: ");
                    String tituloSelecionado = sc.nextLine();
                    boolean tituloEncontrado = false;

                    for (int l = 0; l < i; l++) {
                        if (normalizar(tituloSelecionado).equals(normalizar(tituloDaOrientacao[l]))) {
                            tituloEncontrado = true;

                            String tipoSelecionado = normalizar(tipoDaOrientacao[l]);

                            System.out.println("\n----------------------------------------");
                            switch (tipoSelecionado) {
                                case "manual de operacao":
                                    System.out.println("📝 Descrição: Orientações detalhadas sobre o uso correto e eficiente dos equipamentos.");
                                    System.out.println("📌 Exemplos: Manual de operação de motores, transformadores, geradores, etc.");
                                    break;
                                case "procedimento de seguranca":
                                    System.out.println("🛡️ Descrição: Procedimentos detalhados para garantir a segurança durante a operação de equipamentos e instalações elétricas.");
                                    System.out.println("📌 Exemplos: Procedimento de segurança para instalação elétrica, risco de choque elétrico, etc.");
                                    break;
                                case "manutencao e reparos":
                                    System.out.println("🔧 Descrição: Orientações para a manutenção e reparos de equipamentos, sistemas e dispositivos.");
                                    System.out.println("📌 Exemplos: Manutenção de motores elétricos, geradores de energia, etc.");
                                    break;
                                case "testes e diagnostico":
                                    System.out.println("🧪 Descrição: Procedimentos para testar e diagnosticar problemas em equipamentos e sistemas.");
                                    System.out.println("📌 Exemplos: Teste de diagnóstico de transformadores, automação, etc.");
                                    break;
                                case "manual de conduta e operacoes setoriais":
                                    System.out.println("📘 Descrição: Normas e orientações para a conduta dentro de setores específicos e suas operações.");
                                    System.out.println("📌 Exemplos: Manual de conduta no setor de montagem, etc.");
                                    break;
                                default:
                                    System.out.println("❓ Descrição: Descrição não disponível.");
                            }

                            System.out.println("----------------------------------------");
                            break;
                        }
                    }

                    if (!tituloEncontrado) {
                        System.out.println("\n❌ Título não encontrado!");
                    }
//===========================================================================================================
                
                // 3 EDITAR    
                } else if (menu == 3) {
                    System.out.println("\nEscreva o tipo de orientação que você deseja mudar: ");
                    atualizarOrientacao = sc.nextLine();  

                    for (int h = 0; h < i; h++) {
                        if (atualizarOrientacao.equalsIgnoreCase(tipoDaOrientacao[h])) {
                            System.out.println("\n\nTipo de Orientação selecionada: " + tipoDaOrientacao[h] + "\n\nNovo Tipo: ");
                            atualizarOrientacao = sc.nextLine();  
                            tipoDaOrientacao[h] = atualizarOrientacao;
                        }
                    }
                
                 //===========================================================================================================
                    
                // 4 REMOVER
                } else if (menu == 4) {
                    String produtoRemovido;

                    System.out.println("\n\nItens disponíveis: ");
                    for (int p = 0; p < i; p++) {
                        System.out.println(tituloDaOrientacao[p]);
                    }
                    System.out.println("\nDigite o item que você deseja remover: ");
                    produtoRemovido = sc.nextLine(); 

                    boolean removido = false;

                    for (int k = 0; k < i; k++) {
                        if (tituloDaOrientacao[k].equalsIgnoreCase(produtoRemovido)) {
                            for (int j = k; j < i - 1; j++) { 
                                tituloDaOrientacao[j] = tituloDaOrientacao[j + 1];
                                tipoDaOrientacao[j] = tipoDaOrientacao[j + 1];
                            }
                            tituloDaOrientacao[i - 1] = null;
                            tipoDaOrientacao[i - 1] = null;
                            i--;
                            removido = true;
                            break;
                        }
                    }

                    if (removido) {
                        System.out.println("\nItens após remoção:");
                        for (int p = 0; p < i; p++) {
                            if (tituloDaOrientacao[p] != null) {
                                System.out.println(tituloDaOrientacao[p]);
                            }
                        }
                    } else { 
                        System.out.println("Item " + produtoRemovido + " não encontrado para remover!");
                    }

                 //===========================================================================================================
                    
                 // 5 EXIBIR
                } else if (menu == 5) {

                    System.out.println("\n\n════════════════════════════════════════");
                    System.out.println("     📚 ORIENTAÇÕES CADASTRADAS         ");
                    System.out.println("════════════════════════════════════════");

                    for (int d = 0; d < i; d++) {
                        System.out.println("\n🔖 Título da Orientação: " + tituloDaOrientacao[d]);
                        System.out.println("📂 Tipo da Orientação: " + tipoDaOrientacao[d]);

                        switch (tipoDaOrientacao[d].toLowerCase()) {
                            case "manual de operação":
                                System.out.println("📝 Descrição: Orientações detalhadas sobre o uso correto e eficiente dos equipamentos.");
                                System.out.println("📌 Exemplos: Manual de operação de motores, transformadores, geradores, etc.");
                                break;
                            case "procedimento de segurança":
                                System.out.println("🛡️ Descrição: Procedimentos detalhados para garantir a segurança durante a operação de equipamentos e instalações elétricas.");
                                System.out.println("📌 Exemplos: Procedimento de segurança para instalação elétrica, risco de choque elétrico, etc.");
                                break;
                            case "manutenção e reparos":
                                System.out.println("🔧 Descrição: Orientações para a manutenção e reparos de equipamentos, sistemas e dispositivos.");
                                System.out.println("📌 Exemplos: Manutenção de motores elétricos, geradores de energia, etc.");
                                break;
                            case "testes e diagnóstico":
                                System.out.println("🧪 Descrição: Procedimentos para testar e diagnosticar problemas em equipamentos e sistemas.");
                                System.out.println("📌 Exemplos: Teste de diagnóstico de transformadores, automação, etc.");
                                break;
                            case "manual de conduta e operações setoriais":
                                System.out.println("📘 Descrição: Normas e orientações para a conduta dentro de setores específicos e suas operações.");
                                System.out.println("📌 Exemplos: Manual de conduta no setor de montagem, etc.");
                                break;
                            default:
                                System.out.println("❓ Descrição: Descrição não disponível.");
                        }

                        System.out.println("\n----------------------------------------");
                    }

                
                //===========================================================================================================
                    
                // 6 SAIR
                } else if (menu == 6) {
                    break;
                }
            } while (menu != 6);
 
        }

    }
}


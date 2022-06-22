# teste-avaliador-exp-2
Teste leiloeiro avaliador - replica do livro casa do codigo

Testando o que realmente é necessário
No fim do capítulo passado, escrevemos nosso primeiro teste automatizado de
unidade para a classe Avaliador e garantimos que nosso algoritmo sempre
funcionará para uma lista de lances em ordem crescente. Mas será que só esse
teste é suficiente?
Para confiarmos que a classe Avaliador realmente funciona, pre-
cisamos cobri-la com mais testes. Nesse momento, temos somente um teste.
O cenário do teste nesse caso são 3 lances com os valores 250, 300, 400. Mas
será que se passarmos outros valores, ele continua funcionando? Vamos testar
com 1000, 2000 e 3000. Na mesma classe de testes AvaliadorTest, ape-
nas adicionamos um outro método de testes. É assim que fazemos: cada novo
teste é um novo método. Não apagamos o teste anterior, mas sim criamos um
novo.
import org.junit.Assert;
class AvaliadorTest {
@Test
public void deveEntenderLancesEmOrdemCrescente() {
// código aqui ainda...
}
@Test
public void deveEntenderLancesEmOrdemCrescenteComOutrosValores() {
Usuario joao = new Usuario("Joao");
Usuario jose = new Usuario("José");

Usuario maria = new Usuario("Maria");
Leilao leilao = new Leilao("Playstation 3 Novo");
leilao.propoe(new Lance(maria,1000.0));
leilao.propoe(new Lance(joao,2000.0));
leilao.propoe(new Lance(jose,3000.0));
Avaliador leiloeiro = new Avaliador();
leiloeiro.avalia(leilao);
Assert.assertEquals(3000, leiloeiro.getMaiorLance(), 0.0001);
Assert.assertEquals(1000, leiloeiro.getMenorLance(), 0.0001);
}
}

Ao rodar o teste, vemos que ele passa. Mas será que é suficiente ou pre-
cisamos de mais testes para ordem crescente? Poderíamos escrever vários de-
les, afinal o número de valores que podemos passar para esse cenário é quase
infinito! Poderíamos ter algo como:
class AvaliadorTest {
@Test public void deveEntenderLancesEmOrdemCrescente1() { }
@Test public void deveEntenderLancesEmOrdemCrescente2() { }
@Test public void deveEntenderLancesEmOrdemCrescente3() { }
@Test public void deveEntenderLancesEmOrdemCrescente4() { }
@Test public void deveEntenderLancesEmOrdemCrescente5() { }
// muitos outros testes!
}

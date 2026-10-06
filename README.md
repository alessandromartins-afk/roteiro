using System;
using Xunit;

namespace AulaTestes.Tests
{
    // EXERCÍCIO 1 — VALIDADOR DE SENHA
    public class ValidadorSenhaTests
    {
        [Fact]
        public void Senha123_DeveSerValida()
        {
            var validador = new ValidadorSenha();
            Assert.True(validador.EhValida("Senha123"));
        }

        [Fact]
        public void ApenasNumeros_DeveSerInvalida()
        {
            var validador = new ValidadorSenha();
            Assert.False(validador.EhValida("12345678"));
        }

        [Fact]
        public void SenhaVazia_DeveSerInvalida()
        {
            var validador = new ValidadorSenha();
            Assert.False(validador.EhValida(""));
        }

        [Fact]
        public void ApenasLetras_DeveSerInvalida()
        {
            var validador = new ValidadorSenha();
            Assert.False(validador.EhValida("abcdEFGH"));
        }
    }

    // EXERCÍCIO 2 — CARRINHO DE COMPRAS
    public class CarrinhoTests
    {
        [Fact]
        public void AdicionarItens_DeveSomarTotal()
        {
            var carrinho = new Carrinho();

            carrinho.Adicionar(new Item { Nome = "Produto A", Preco = 10 });
            carrinho.Adicionar(new Item { Nome = "Produto B", Preco = 20 });

            Assert.Equal(30, carrinho.Total());
        }

        [Fact]
        public void Limpar_DeveZerarCarrinho()
        {
            var carrinho = new Carrinho();

            carrinho.Adicionar(new Item { Nome = "Produto A", Preco = 10 });
            carrinho.Limpar();

            Assert.Equal(0, carrinho.Quantidade());
        }

        [Fact]
        public void Quantidade_DeveRetornarNumeroCorreto()
        {
            var carrinho = new Carrinho();

            carrinho.Adicionar(new Item { Nome = "Produto A", Preco = 10 });
            carrinho.Adicionar(new Item { Nome = "Produto B", Preco = 20 });

            Assert.Equal(2, carrinho.Quantidade());
        }
    }

    // EXERCÍCIO 3 — CONVERSOR DE TEMPERATURA
    public class ConversorTemperaturaTests
    {
        [Fact]
        public void Celsius0_DeveRetornar32F()
        {
            var conversor = new ConversorTemperatura();
            var resultado = conversor.CelsiusParaFahrenheit(0);

            Assert.Equal(32, resultado, 2);
        }

        [Fact]
        public void Celsius100_DeveRetornar212F()
        {
            var conversor = new ConversorTemperatura();
            var resultado = conversor.CelsiusParaFahrenheit(100);

            Assert.Equal(212, resultado, 2);
        }

        [Fact]
        public void Fahrenheit32_DeveRetornar0C()
        {
            var conversor = new ConversorTemperatura();
            var resultado = conversor.FahrenheitParaCelsius(32);

            Assert.Equal(0, resultado, 2);
        }

        [Fact]
        public void Fahrenheit212_DeveRetornar100C()
        {
            var conversor = new ConversorTemperatura();
            var resultado = conversor.FahrenheitParaCelsius(212);

            Assert.Equal(100, resultado, 2);
        }
    }

    // EXERCÍCIO 4 — CALCULADORA DE IMC
    public class CalculadoraIMCTests
    {
        [Fact]
        public void Calcular_DeveRetornar22_86()
        {
            var calc = new CalculadoraIMC();
            var resultado = calc.Calcular(70, 1.75);

            Assert.Equal(22.86, resultado, 2);
        }

        [Fact]
        public void Classificar17_DeveRetornarAbaixoDoPeso()
        {
            var calc = new CalculadoraIMC();

            Assert.Equal("Abaixo do peso", calc.Classificar(17));
        }

        [Fact]
        public void Classificar26_DeveRetornarSobrepeso()
        {
            var calc = new CalculadoraIMC();

            Assert.Equal("Sobrepeso", calc.Classificar(26));
        }

        [Fact]
        public void AlturaZero_DeveLancarExcecao()
        {
            var calc = new CalculadoraIMC();

            Assert.Throws<ArgumentException>(
                () => calc.Calcular(70, 0)
            );
        }
    }
}
### Olá, Eu sou o Diogo Santana e este é o meu portifólio em desenvolvimento! 😊

[![Email](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](https://mail.google.com/mail/u/2/#inbox?compose=VpCqJKjnHcszJTKgfCzWvRtvkrMBgBhLjXhdxkmkGJjbfbLSWhvTHGwqsJDtSnWbXflsQvq)
[![Linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/diogo-santana-aa26a8187/)
[![Whatsapp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/5541992152784)
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/diogo_reisssss/)

![DiogoReisDev GitHub stats](https://github-readme-stats.vercel.app/api?username=DiogoReisDev&show_icons=true&theme=transparent)

## Linguagem que estou me especializando:

<div style="display: inline_block"><br/>
    <img text-align="center" alt="Python" src="https://img.shields.io/badge/Python-14354C?style=for-the-badge&logo=python&logoColor=white" /><br/>

## Linguagens e Tecnologias complementares:

</div style="display: inline_block"><br/>
    <img text-align="center" alt="CSS3" src="https://img.shields.io/badge/CSS-239120?&style=for-the-badge&logo=css3&logoColor=white" />
    <img text-align="center" alt="HTML5" src="https://img.shields.io/badge/HTML-239120?style=for-the-badge&logo=html5&logoColor=white" />
    <img text-align="center" alt="SQLite" src="https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white" />
    <img text-align="center" alt="Django" src="https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white" />
</div><br/>

Simplesmente um garoto Apaixonado por tecnologia com fome por conhecimento!

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.js"></script>
  <title>Globo de Plasma</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background-color: black;
    }
  </style>
</head>
<body>
  <script>
    let particles = [];
    let stars = [];

    function setup() {
      createCanvas(window.innerWidth, window.innerHeight);

      // Cria estrelas
      for (let i = 0; i < 200; i++) {
        stars.push(createVector(random(width), random(height)));
      }
    }

    function draw() {
      // Desenha estrelas
      fill(255);
      noStroke();
      for (let i = 0; i < stars.length; i++) {
        ellipse(stars[i].x, stars[i].y, 2, 2);
      }

      // Adiciona uma nova partícula na posição do mouse
      particles.push(new Particle(mouseX, mouseY));

      // Atualiza e exibe todas as partículas
      for (let i = particles.length - 1; i >= 0; i--) {
        particles[i].update();
        particles[i].display();

        // Remove partículas antigas
        if (particles[i].lifespan <= 0) {
          particles.splice(i, 1);
        }
      }
    }

    // Define a classe Particle
    class Particle {
      constructor(x, y) {
        this.x = x;
        this.y = y;
        this.vx = random(-1, 1);
        this.vy = random(-1, 1);
        this.alpha = 255;
        this.size = random(2, 5);
        this.lifespan = 150; // Adiciona uma vida para a partícula
        this.color = color(random(50, 100), random(150, 200), random(200, 255), this.alpha);
      }

      update() {
        this.x += this.vx;
        this.y += this.vy;
        this.alpha -= 2; // Reduz a opacidade gradualmente
        this.lifespan -= 1; // Reduz a vida da partícula

        // Reduz ainda mais a opacidade conforme o tempo passa
        this.alpha = map(this.lifespan, 0, 150, 0, 255);
      }

      display() {
        noStroke();
        fill(this.color.levels[0], this.color.levels[1], this.color.levels[2], this.alpha);
        ellipse(this.x, this.y, this.size, this.size);

        // Adiciona detalhes delicados como pequenos elipses
        fill(255, this.alpha);
        ellipse(this.x + random(-this.size, this.size), this.y + random(-this.size, this.size), 1, 1);
      }
    }
  </script>
</body>
</html>

<div align="center">
<img src="https://github.com/1337thai/css/blob/master/ai.gif?raw=true" align="center" style="width: 100%" />
</div>  
  

### <div align="center">I'm Thaina, a dev student from Brazil 👩‍💻
</div>  
  

- 🌱 I’m currently learning JavaScript, C#, MySQL  
  

- ⚡ Fun fact: I love Capybaras  
  

<br/>  


## My Skill Set  
<table><tr><td valign="top" width="33%">



### Frontend  
<div align="center">  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/html5-original-wordmark.svg" alt="HTML5" height="50" />  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/css3-original-wordmark.svg" alt="CSS3" height="50" />  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/javascript-original.svg" alt="JavaScript" height="50" />  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/bootstrap-plain.svg" alt="Bootstrap" height="50" />  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/typescript-original.svg" alt="TypeScript" height="50" />  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/react-original-wordmark.svg" alt="React" height="50" />  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/photoshop-plain.svg" alt="Photoshop" height="50" />  
</div>

</td><td valign="top" width="33%">



### Backend  
<div align="center">  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/cplusplus-original.svg" alt="C++" height="50" />  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/express-original-wordmark.svg" alt="Express.js" height="50" />  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/nodejs-original-wordmark.svg" alt="Node.js" height="50" />  
</div>

</td><td valign="top" width="33%">



### DataBase  
<div align="center">  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/mariadb.png" alt="Maria DB" height="50" />  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/mysql-original-wordmark.svg" alt="MySQL" height="50" />  
</div>  



### Tools  
<div align="center">  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/linux-original.svg" alt="Linux" height="50" />  
<img style="margin: 10px" src="https://profilinator.rishav.dev/skills-assets/git-scm-icon.svg" alt="Git" height="50" />  
</div>

</td></tr></table>  

<br/>  


## Connect with me  
<div align="center">
<a href="https://linkedin.com/in/thainaraujo" target="_blank">
<img src=https://img.shields.io/badge/linkedin-%231E77B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white alt=linkedin style="margin-bottom: 5px;" />
</a>
<a href="https://github.com/1337thai" target="_blank">
<img src=https://img.shields.io/badge/github-%2324292e.svg?&style=for-the-badge&logo=github&logoColor=white alt=github style="margin-bottom: 5px;" />
</a>  
</div>  
  

<br/>  


## Github Stats  
<div align="center"><img src="https://github-readme-stats.vercel.app/api?username=1337thai&show_icons=true&count_private=true&hide_border=true" align="center" /></div>  

<br/>  


## Recent Blog Posts  
  

<br/>  

<br/>  

<div align="center">
<img src="https://komarev.com/ghpvc/?username=1337thai&&style=flat-square" align="center" />
</div>  
  

<br/>  


<br />

----
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.util.Random;

public class jogocobrinha extends JFrame implements ActionListener, KeyListener {

    private final int LARGURA_TELA = 300;
    private final int ALTURA_TELA = 300;
    private final int TAMANHO_BLOCO = 10;
    private final int NUMERO_BLOCOS = LARGURA_TELA * ALTURA_TELA / (TAMANHO_BLOCO * TAMANHO_BLOCO);
    private int[] xCobrinha = new int[NUMERO_BLOCOS];
    private int[] yCobrinha = new int[NUMERO_BLOCOS];
    private int tamanhoCobrinha = 3;
    private int macaX;
    private int macaY;
    private boolean emJogo = true;
    private Timer timer;

    public jogocobrinha() {
        setTitle("Jogo da Cobrinha");
        setSize(LARGURA_TELA, ALTURA_TELA);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);
        setResizable(false);

        addKeyListener(this);
        setFocusable(true);

        inicializarJogo();
        timer = new Timer(100, this);
        timer.start();
    }

    private void inicializarJogo() {
        emJogo = true;
        tamanhoCobrinha = 3;

        for (int i = 0; i < tamanhoCobrinha; i++) {
            xCobrinha[i] = 50 - i * TAMANHO_BLOCO;
            yCobrinha[i] = 50;
        }

        gerarMaca();
    }

    private void gerarMaca() {
        Random random = new Random();
        macaX = random.nextInt(LARGURA_TELA / TAMANHO_BLOCO) * TAMANHO_BLOCO;
        macaY = random.nextInt(ALTURA_TELA / TAMANHO_BLOCO) * TAMANHO_BLOCO;
    }

    private void mover() {
        for (int i = tamanhoCobrinha; i > 0; i--) {
            xCobrinha[i] = xCobrinha[i - 1];
            yCobrinha[i] = yCobrinha[i - 1];
        }

        switch (direcao) {
            case KeyEvent.VK_UP:
                yCobrinha[0] -= TAMANHO_BLOCO;
                break;
            case KeyEvent.VK_DOWN:
                yCobrinha[0] += TAMANHO_BLOCO;
                break;
            case KeyEvent.VK_LEFT:
                xCobrinha[0] -= TAMANHO_BLOCO;
                break;
            case KeyEvent.VK_RIGHT:
                xCobrinha[0] += TAMANHO_BLOCO;
                break;
        }
    }

    private void checarColisao() {
        // Checar colisão com as bordas da tela
        if (xCobrinha[0] >= LARGURA_TELA || xCobrinha[0] < 0 || yCobrinha[0] >= ALTURA_TELA || yCobrinha[0] < 0) {
            emJogo = false;
        }

        // Checar colisão com o corpo da cobrinha
        for (int i = 1; i < tamanhoCobrinha; i++) {
            if (xCobrinha[0] == xCobrinha[i] && yCobrinha[0] == yCobrinha[i]) {
                emJogo = false;
            }
        }

        // Checar colisão com a maçã
        if (xCobrinha[0] == macaX && yCobrinha[0] == macaY) {
            tamanhoCobrinha++;
            gerarMaca();
        }
    }

    private void desenhar(Graphics g) {
        if (emJogo) {
            // Desenhar a maçã
            g.setColor(Color.RED);
            g.fillRect(macaX, macaY, TAMANHO_BLOCO, TAMANHO_BLOCO);

            // Desenhar a cobrinha
            for (int i = 0; i < tamanhoCobrinha; i++) {
                if (i == 0) {
                    g.setColor(Color.GREEN);
                } else {
                    g.setColor(Color.YELLOW);
                }
                g.fillRect(xCobrinha[i], yCobrinha[i], TAMANHO_BLOCO, TAMANHO_BLOCO);
            }
        } else {
            // Se o jogo acabou, exibir uma mensagem
            g.setColor(Color.RED);
            g.setFont(new Font("Arial", Font.BOLD, 20));
            g.drawString("Game Over", 100, ALTURA_TELA / 2);
        }
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        if (emJogo) {
            mover();
            checarColisao();
        }

        repaint();
    }

    @Override
    public void paint(Graphics g) {
        super.paint(g);
        desenhar(g);
    }

    private int direcao = KeyEvent.VK_RIGHT;

    @Override
    public void keyPressed(KeyEvent e) {
        int key = e.getKeyCode();

        if ((key == KeyEvent.VK_LEFT) && (direcao != KeyEvent.VK_RIGHT)) {
            direcao = KeyEvent.VK_LEFT;
        } else if ((key == KeyEvent.VK_RIGHT) && (direcao != KeyEvent.VK_LEFT)) {
            direcao = KeyEvent.VK_RIGHT;
        } else if ((key == KeyEvent.VK_UP) && (direcao != KeyEvent.VK_DOWN)) {
            direcao = KeyEvent.VK_UP;
        } else if ((key == KeyEvent.VK_DOWN) && (direcao != KeyEvent.VK_UP)) {
            direcao = KeyEvent.VK_DOWN;
        }
    }

    @Override
    public void keyReleased(KeyEvent e) {
        // Não é necessário implementar neste exemplo
    }

    @Override
    public void keyTyped(KeyEvent e) {
        // Não é necessário implementar neste exemplo
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            new jogocobrinha().setVisible(true);
        });
    }
}

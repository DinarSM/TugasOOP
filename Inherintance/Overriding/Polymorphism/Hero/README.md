package TugasInherintanceOverridingPolymorphismHero;

/**
 *
 * @author DINAR
 */
public class Hero {
    String name;
    double attackPower, health;

    Hero(String nameInput, double attackInput, double healthInput){
        name = nameInput;
        attackPower = attackInput;
        health = healthInput;
    }

    void Menyerang(Hero enemy){
        System.out.println("\n" + name + " menyerang " + enemy.name);
        enemy.kerusakan(attackPower);
    }

    void kerusakan(double kerusakan){
        System.out.println(name + " mengalami kerusakan sebesar : " + kerusakan);
        health -= kerusakan;
    }

    void Output(){
        System.out.println("\nName: " + name);
        System.out.println("Health: " + health);
        System.out.println("Power: " + attackPower);
    }
}

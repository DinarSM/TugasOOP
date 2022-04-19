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




package TugasInherintanceOverridingPolymorphismHero;

/**
 *
 * @author DINAR
 */
public class HeroPower extends Hero{
    String type = "SuperPower";

    HeroPower(String nameInput, double attackInput, double healthInput){
	super(nameInput, attackInput, healthInput);
    }

   @Override
    void Output(){
        super.Output();
        System.out.println("Type : " + type);
    }

    @Override
    void Menyerang(Hero enemy){
        System.out.println("\n" + name + " menyerang " + enemy.name);
        enemy.kerusakan(attackPower*2);
    }

    @Override
    void kerusakan(double kerusakan){
        System.out.println(name + " mengalami kerusakan sebesar : " + kerusakan);
        health -= kerusakan;   
    }
}




package TugasInherintanceOverridingPolymorphismHero;

/**
 *
 * @author DINAR
 */
public class HeroStrength extends Hero{
    String type = "Strength";

    HeroStrength(String nameInput, double attackInput, double healthInput){
        super(nameInput, attackInput, healthInput);
    }

    @Override
    void Output(){
        super.Output();
        System.out.println("Type : " + type);
    }

    @Override
    void kerusakan(double kerusakan){
        System.out.println(name + " mengalami kerusakan sebesar : " + kerusakan + " -> " + 0.5*kerusakan);
        health -= 0.5*kerusakan;
    }
}





package TugasInherintanceOverridingPolymorphismHero;

/**
 *
 * @author DINAR
 */
public class NewMain {
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        Hero hero1 = new Hero("Natalia",10,100);
	HeroStrength hero2 = new HeroStrength("Zilong", 20, 100);
        //polymorphism
        Hero hero3 = new HeroPower("Argus", 15,100);


        Hero[] KumpulanHero = new Hero[3];
        KumpulanHero[0] = hero1;
        KumpulanHero[1] = hero2;
        KumpulanHero[2] = hero3;    

        System.out.print("\n" + "PILIHAN HERO :");    
        KumpulanHero[0].Output();
	KumpulanHero[1].Output();
	KumpulanHero[2].Output();

        System.out.print("\n" + "Serangan :"); 
        hero1.Menyerang(hero3);   
        hero3.Menyerang(hero1);   
        hero2.Menyerang(hero1);


        System.out.print("\n" + "Kondisi Hero Setelah Serangan :");
        KumpulanHero[0].Output();
        KumpulanHero[1].Output();
        KumpulanHero[2].Output();
    }
}

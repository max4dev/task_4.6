# task_4.6


public class Main {

    public static void main(String[] args) {


        Person valera=new Person("Валера","Иванов",69,null,null);
        Person olga = new Person("Ольга","Иванова",67,null,null);
        Person oleg = new Person("Олег","Петров",65,null,null);
        Person jula = new Person("Юля","Петрова",67,null,null);
        Person alex = new Person("Алексей","Иванов",37,olga,valera);
        Person eva  = new Person("Ева","Иванова",37,jula,oleg);
        Person gosha= new Person("Гоша","Иванов",10,eva,alex);
        System.out.println("Мама Алексея: "+alex.getMother().getName());
        System.out.println("Бабушка Гоши: "+gosha.getMother().getMother().getName());

        gosha.getInfo();
    }
}

class Person {
    private String name;
    private String lastname;
    private int age;
    private int hp = 100;
    private Person mother;
    private Person father;

    public Person(String name, String lastname, int age, Person mother, Person father) {
        this.name = name;
        this.lastname = lastname;
        this.age = age;
        this.mother = mother;
        this.father = father;
    }

    public void getInfo() {
        String info = "Меня зовут " + this.name + "\n";
        if (this.mother != null) {
            info += "Имя моей мамы " + this.mother.name + "\n";
        }
        if (this.father != null) {
            info += "Моего папу зовут " + this.father.name + "\n";
        }

        String babushkaFather = "";
        String babushkaMother = "";
        if (this.mother.mother != null) {
            babushkaMother = this.mother.mother.name;
        }
        if (this.father.mother != null) {
            babushkaFather = this.father.mother.name;
        }

        String dedushkaFather = "";
        String dedushkaMother = "";

        if (this.father.father != null) {
            dedushkaMother = this.mother.father.name;
        }
        if (this.father.father != null) {
            dedushkaFather = this.father.father.name;
        }
        info += "У меня две бабушки, бабушка " + babushkaFather + " и бабубшка " + babushkaMother + "\n";
        info += "У меня два дедушки, дедушка " + dedushkaFather + " и дедушка " + dedushkaMother + "\n";

        System.out.println(info);
    }

    public String getName() {
        return this.name;
    }

    public int getHp() {
        return this.hp;
    }

    public Person getMother() {
        return this.mother;
    }

    public void setHp(int hp) {
        if (this.hp + hp > 100) this.hp = 100;
        else this.hp = this.hp + hp;
    }
}

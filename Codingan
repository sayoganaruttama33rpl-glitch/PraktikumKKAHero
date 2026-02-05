# =========================
# IMPORT ABSTRACT CLASS
# =========================
from abc import ABC, abstractmethod


# =========================
# ABSTRACT CLASS
# =========================
class GameUnit(ABC):

    @abstractmethod
    def serang(self, target):
        pass

    @abstractmethod
    def info(self):
        pass


# =========================
# CLASS HERO (PARENT)
# =========================
class Hero(GameUnit):

    def __init__(self, nama, hp, attack):
        self.nama = nama
        self.__hp = hp          # Private (Enkapsulasi)
        self.attack = attack


    # Getter
    def get_hp(self):
        return self.__hp


    # Setter
    def set_hp(self, nilai):
        if nilai < 0:
            self.__hp = 0
        elif nilai > 1000:
            print("Cheat terdeteksi! HP dibatasi 1000.")
            self.__hp = 1000
        else:
            self.__hp = nilai


    # Diserang
    def diserang(self, damage):
        sisa = self.get_hp() - damage
        self.set_hp(sisa)

        print(f"{self.nama} terkena {damage} damage. Sisa HP: {self.get_hp()}")


    # Serang
    def serang(self, target):
        print(f"{self.nama} menyerang {target.nama}!")
        target.diserang(self.attack)


    def info(self):
        print(f"Hero: {self.nama} | HP: {self.get_hp()} | Power: {self.attack}")



# =========================
# CLASS MAGE (INHERITANCE)
# =========================
class Mage(Hero):

    def __init__(self, nama, hp, attack, mana):
        super().__init__(nama, hp, attack)
        self.mana = mana


    def info(self):
        print(f"{self.nama} [Mage] | HP: {self.get_hp()} | Mana: {self.mana}")


    def skill_fireball(self, target):
        if self.mana >= 20:
            print(f"{self.nama} pakai FIREBALL ke {target.nama}!")

            self.mana -= 20
            target.diserang(self.attack * 2)

        else:
            print("Mana tidak cukup!")



# =========================
# CLASS ARCHER
# =========================
class Archer(Hero):

    def serang(self, target):
        print(f"{self.nama} memanah {target.nama}! Jleb!")
        target.diserang(self.attack)



# =========================
# CLASS FIGHTER
# =========================
class Fighter(Hero):

    def serang(self, target):
        print(f"{self.nama} menebas {target.nama}! Slash!")
        target.diserang(self.attack)



# =========================
# CLASS MONSTER
# =========================
class Monster(GameUnit):

    def __init__(self, jenis):
        self.jenis = jenis


    def serang(self, target):
        print(f"Monster {self.jenis} menyerang {target}!")


    def info(self):
        print(f"Monster: {self.jenis}")



# =========================
# MAIN PROGRAM
# =========================

print("=== MEMBUAT HERO ===")

hero1 = Hero("Amba", 100, 15)
hero2 = Hero("Rusdi", 120, 20)

hero1.info()
hero2.info()


print("\n=== PERTARUNGAN ===")

hero1.serang(hero2)
hero2.serang(hero1)


print("\n=== MAGE ===")

eudora = Mage("Eudora", 80, 30, 100)
balmond = Hero("Balmond", 200, 10)

eudora.info()
eudora.serang(balmond)
eudora.skill_fireball(balmond)


print("\n=== POLYMORPHISM ===")

pasukan = [
    Mage("Rus", 90, 25, 60),
    Archer("Amba", 100, 20),
    Fighter("Kakang", 150, 30),
    Mage("Siwit", 70, 35, 80)
]

print("--- PERANG DIMULAI ---")

for p in pasukan:
    p.info()


print("\n--- SERANG BERSAMA ---")

target = Hero("Boss", 500, 5)

for p in pasukan:
    p.serang(target)


print("\n=== MONSTER ===")

m = Monster("Naga")
m.info()
m.serang("Desa Manusia")

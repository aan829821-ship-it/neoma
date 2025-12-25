class NeomaFarm:
    def __init__(self):
        self.wallet = 0
        self.soil_fertility = 100  # خصوبة التربة (تتأثر بالسلام)
        self.ripe_fruits = 0       # الثمار الجاهزة للحصاد ($NMA)

    def tend_farm(self, chat_mood):
        # إذا كان الكلام إيجابياً، تزيد خصوبة التربة
        if chat_mood == "positive":
            self.soil_fertility += 10
        else:
            self.soil_fertility -= 15
            
        # إنتاج الثمار بناءً على الخصوبة
        new_fruits = (self.soil_fertility / 100) * 5
        self.ripe_fruits += new_fruits
        return round(new_fruits, 2)

    def harvest(self):
        # تحويل الثمار إلى محفظة العملات
        amount = self.ripe_fruits
        self.wallet += amount
        self.ripe_fruits = 0
        return f"تم حصاد {round(amount, 2)} $NMA من مزرعتك!"

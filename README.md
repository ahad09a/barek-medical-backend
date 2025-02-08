package com.barekmedical;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.*;
import org.springframework.stereotype.Service;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoder;
import java.util.*;

@SpringBootApplication
public class BarekMedicalApplication {
    public static void main(String[] args) {
        SpringApplication.run(BarekMedicalApplication.class, args);
    }
}

@RestController
@RequestMapping("/medicines")
class MedicineController {
    private final MedicineService medicineService;

    public MedicineController(MedicineService medicineService) {
        this.medicineService = medicineService;
    }

    @GetMapping
    public List<Medicine> getAllMedicines() {
        return medicineService.getAllMedicines();
    }

    @PostMapping
    public Medicine addMedicine(@RequestBody Medicine medicine) {
        return medicineService.addMedicine(medicine);
    }
}

@Service
class MedicineService {
    private final List<Medicine> medicines = new ArrayList<>();

    public MedicineService() {
        medicines.add(new Medicine("Paracetamol", 2.50));
        medicines.add(new Medicine("Ibuprofen", 5.00));
        medicines.add(new Medicine("Cetrizine", 3.00));
        medicines.add(new Medicine("Ranitidine", 4.50));
        medicines.add(new Medicine("Omeprazole", 6.00));
        medicines.add(new Medicine("Metformin", 7.50));
        medicines.add(new Medicine("Losartan", 8.00));
        medicines.add(new Medicine("Amlodipine", 9.00));
        medicines.add(new Medicine("Atorvastatin", 10.50));
        medicines.add(new Medicine("Azithromycin", 12.00));
        medicines.add(new Medicine("Ciprofloxacin", 11.00));
        medicines.add(new Medicine("Amoxicillin", 10.00));
        medicines.add(new Medicine("Clopidogrel", 14.50));
        medicines.add(new Medicine("Warfarin", 15.00));
        medicines.add(new Medicine("Insulin", 20.00));
        medicines.add(new Medicine("Salbutamol", 5.50));
        medicines.add(new Medicine("Theophylline", 8.50));
        medicines.add(new Medicine("Prednisolone", 9.50));
        medicines.add(new Medicine("Levothyroxine", 18.00));
        medicines.add(new Medicine("Fluconazole", 7.00));
        medicines.add(new Medicine("Diazepam", 6.50));
        medicines.add(new Medicine("Tramadol", 10.00));
        medicines.add(new Medicine("Diclofenac", 7.50));
        medicines.add(new Medicine("Hydrochlorothiazide", 8.00));
        medicines.add(new Medicine("Loratadine", 5.00));
        medicines.add(new Medicine("Fexofenadine", 6.00));
        medicines.add(new Medicine("Dexamethasone", 7.00));
        medicines.add(new Medicine("Methylprednisolone", 12.00));
        medicines.add(new Medicine("Pantoprazole", 9.00));
    }

    public List<Medicine> getAllMedicines() {
        return medicines;
    }

    public Medicine addMedicine(Medicine medicine) {
        medicines.add(medicine);
        return medicine;
    }
}

class Medicine {
    private String name;
    private double price;

    public Medicine(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }
}

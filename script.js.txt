// 1. Create dummy student records

const dummyStudents = [
    {
        studentId: "12345",
        name: "Lekoba Ethan",
        regNo: "S26b23/164",
        course: "Computer Science",
        faceDescriptor: null
    },
    {
        studentId: "12346",
        name: "GLENN TWESIIME",
        regNo: "",
        course: "Data Science",
        faceDescriptor: null
    },
    {
        studentId: "12347",
        name: "Asaba Ian",
        regNo: "S26B23/072",
        course: "Computer Science",
        faceDescriptor: null
    }
];

// 2. Save records in browser storage

if (!localStorage.getItem("lvasStudents")) {
    localStorage.setItem(
        "lvasStudents",
        JSON.stringify(dummyStudents)
    );
}

// 3. Retrieve student records

function getStudents() {
    return JSON.parse(
        localStorage.getItem("lvasStudents")
    );
}
function registerStudent(studentId, name, regNo, course, descriptor) {

    let students = getStudents();

    // Check whether student already exists
    if (students.some(s => s.studentId === studentId)) {
        alert("Student already registered!");
        return;
    }

    let newStudent = {
        studentId: studentId,
        name: name,
        regNo: regNo,
        course: course,
        faceDescriptor: Array.from(descriptor)
    };

    students.push(newStudent);

    localStorage.setItem(
        "lvasStudents",
        JSON.stringify(students)
    );

    alert("Student registered successfully!");
}
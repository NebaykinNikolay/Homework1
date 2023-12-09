class Student:
  def __init__(self, name, surname, gender):
      self.name = name
      self.surname = surname
      self.gender = gender
      self.finished_courses = []
      self.courses_in_progress = []
      self.grades = {}



class Mentor:
  def __init__(self, name, surname):
      self.name = name
      self.surname = surname
      self.courses_attached = []



class Lecturer(Mentor):
  pass

class Rewiewer(Mentor):
        def rate_hw(self, student, course, grade):
          if isinstance(student, Student) and course in self.courses_attached and course in student.courses_in_progress:
              if course in student.grades:
                  student.grades[course] += [grade]
              else:
                  student.grades[course] = [grade]
          else:
              return 'Ошибка'


best_student = Student('Roy', 'Eman', 'your_gender')
best_student.courses_in_progress += ['Python']

cool_mentor = Rewiewer('Victor', 'Ivanov')
cool_mentor.courses_attached += ['Python']

cool_mentor.rate_hw(best_student, 'Python', 10)
cool_mentor.rate_hw(best_student, 'Python', 10)
cool_mentor.rate_hw(best_student, 'Python', 10)

print(best_student.grades)
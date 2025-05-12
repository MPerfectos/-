``` mermaid
    classDiagram
    class User {
        -int userId
        -String email
        -String password
        -String fullName
        -String phoneNumber
        -Date registrationDate
        
    }

    class Employee {
        -String resume
        -List~Skill~ skills
        -List~WorkExperience~ experiences
        -List~Education~ education
        -List~JobApplication~ applications
        
    }

    class Employer {
        -String companyName
        -String companyDescription
        -String industry
        -String companySize
        -String companyLocation
        -List~JobPosting~ jobPostings
        
    }

    class JobPosting {
        -int jobId
        -String title
        -String description
        -String requirements
        -String location
        -double salary
        -Date postingDate
        -Date expiryDate
        -List~JobApplication~ applications
        
    }

    class JobApplication {
        -int applicationId
        -Date applicationDate
        -String coverLetter
        
    }

    class Skill {
        -String name
        -int proficiencyLevel
        -String description
    }

    class WorkExperience {
        -String companyName
        -String position
        -Date startDate
        -Date endDate
        -String description
    }

    class Education {
        -String institution
        -String degree
        -String field
        -Date startDate
        -Date endDate
        -double average
    }

    class Notification {
        -int notificationId
        -String message
        -Date timestamp
        -boolean isRead
    }

    class Message {
        -int messageId
        -String content
        -Date timestamp
        -boolean isRead  
    }


    %% Relationships
    User <|-- Employee
    User <|-- Employer
    Employer "1" -- "*" JobPosting : posts
    JobPosting "1" -- "*" JobApplication : receives
    Employee "1" -- "*" JobApplication : submits
    Employee "1" -- "*" Skill : has
    Employee "1" -- "*" WorkExperience : has
    Employee "1" -- "*" Education : has
    User "1" -- "*" Notification : receives
    User "1" -- "*" Message : sends
    User "1" -- "*" Message : receives
```
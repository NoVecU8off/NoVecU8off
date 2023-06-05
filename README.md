```rust
use std::collections::HashMap;

pub struct About {
    name: String,
    surname: String,
    age: u8,
    career: Career,
    experience: Experience,
    projects: Projects,
    hobbies: Hobbies,
}

impl About {
    pub fn new() -> Self {
        About {
            name: String::from("Andrey"),
            surname: String::from("Novikov"),
            age: 21,
            career: Career::new(),
            experience: Experience::new(),
            projects: Projects::new(),
            hobbies: Hobbies::new(),
        }
    }
}

pub struct Career {
    position: String,
}

impl Career {
    pub fn new() -> Self {
        Career {
            position: String::from("Programmer"),
        }
    }
}

pub struct Language {
    name: String,
}

impl Language {
    pub fn new(name: &str) -> Self {
        Language {
            name: String::from(name),
        }
    }
}

pub struct Experience {
    language_experience: HashMap<Language, u32>,
}

impl Experience {
    pub fn new() -> Self {
        let mut language_experience = HashMap::new();
        language_experience.insert(Language::new("Solidity"), 10); // as months
        language_experience.insert(Language::new("Rust"), 4); // as months
        language_experience.insert(Language::new("Golang"), 1); // as months (at least I can read Go)

        Experience {
            language_experience,
        }
    }
}

pub enum Status {
    Complete,
    InProgress,
}

pub struct Project {
    name: String,
    status: Status,
    language: Language,
    github_link: String,
}

impl Project {
    pub fn new(name: &str, status: Status, language: Language, github_link: &str) -> Self {
        Project {
            name: String::from(name),
            status,
            language,
            github_link: String::from(github_link),
        }
    }
}

pub struct Projects {
    project_list: Vec<Project>,
}

impl Projects {
    pub fn new() -> Self {
        Projects {
            project_list: vec![
                Project::new("Vector", Status::InProgress, Language::new("Rust"), "https://github.com/NoVecU8off/Vector"),
                Project::new("CryptoTron", Status::Complete, Language::new("Solidity"), "https://github.com/NoVecU8off/CryptoTron"),
                Project::new("CryptoSwap", Status::Complete, Language::new("Solidity"), "https://github.com/NoVecU8off/CryptoSwap"),
                Project::new("CryptoRoulette", Status::Complete, Language::new("Solidity"), "https://github.com/NoVecU8off/CryptoRoulette"),
                Project::new("Tokenizer", Status::Complete, Language::new("Solidity"), "https://github.com/NoVecU8off/Tokenizer"),
            ],
        }
    }
}

pub struct Hobbies {
    hobbies_list: Vec<String>,
}

impl Hobbies {
    pub fn new() -> Self {
        Hobbies {
            hobbies_list: vec![String::from("Reading"), String::from("Programming"), String::from("Learning"), String::from("Music")],
        }
    }
}

fn main() {
    let about = About::new();
    println!("{:#?}", about);
}

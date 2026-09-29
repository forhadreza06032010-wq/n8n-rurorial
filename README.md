use serde::{Deserialize, Serialize};
use std::collections::HashMap;

#[derive(Serialize, Deserialize, Debug)]
struct PackageJson {
    name: String,
    private: bool,
    version: String,
    engines: HashMap<String, String>,
    scripts: HashMap<String, String>,
    dependencies: HashMap<String, String>,
}

fn main() {
    let mut engines = HashMap::new();
    engines.insert("node".to_string(), ">=18".to_string());

    let mut scripts = HashMap::new();
    scripts.insert("start".to_string(), "n8n start".to_string());

    let mut dependencies = HashMap::new();
    dependencies.insert("n8n".to_string(), "^1.0.0".to_string());

    let package = PackageJson {
        name: "n8n-on-render".to_string(),
        private: true,
        version: "1.0.0".to_string(),
        engines,
        scripts,
        dependencies,
    };

    // ডাটাটি JSON স্ট্রিং হিসেবে দেখতে:
    let json_output = serde_json::to_string_pretty(&package).unwrap();
    println!("{}", json_output);
}

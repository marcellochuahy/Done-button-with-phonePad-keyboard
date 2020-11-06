# Done button with phonePad keyboard

```
import UIKit

class ViewController: UIViewController {
    
    @IBOutlet weak var textField: UITextField!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        setupTextField()
    }
    
}

extension ViewController: UITextFieldDelegate {
    
    private func setupTextField() {
        textField.keyboardType = .phonePad
        textField.inputAccessoryView = inputAccessoryView()
        textField.delegate = self
    }
    
    private func inputAccessoryView() -> UIToolbar {
        let keyboardToolbar = UIToolbar()
        keyboardToolbar.sizeToFit()
        keyboardToolbar.isTranslucent = false
        let flexBarButton = UIBarButtonItem(barButtonSystemItem: .flexibleSpace, target: nil, action: nil)
        let doneBarButton = UIBarButtonItem(title: "Fechar", style: .done, target: self, action: #selector(endEditing(_:)))
        keyboardToolbar.items = [flexBarButton, doneBarButton]
        return keyboardToolbar
    }
    
    @objc private func endEditing(_ sender: UIView) {
        self.view.endEditing(true)
    }
    
}



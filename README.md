# Comment Generation Model

A Python script for generating realistic, context-aware comments on topics, images, or video content using the Llama-3.2-3B-Instruct language model and Salesforce BLIP image captioning. This model is designed to simulate social media comment sections (like YouTube or TikTok), supporting positive, engaging, and natural-sounding responses.

## 🚀 Features

- **Text and Image Context:** Generates comments based on topic, description, and optionally an image or a previous comment.
- **Image-to-Text:** Uses BLIP image captioning to convert images into descriptive text for richer comment context.
- **Customizable Usernames:** Selects usernames from a provided list for realism.
- **Natural Language Output:** Ensures comments are formatted realistically (e.g., "Username: Comment").
- **Validation:** Checks output to ensure it matches expected comment structure.
- **Efficient Inference:** Fast on GPU (T4: ~1.1s per comment).

## 🧩 Main Components

- `create_prompt(...)`: Builds a prompt for the language model, optionally including a previous comment for conversational threads.
- `is_valid_message(message)`: Validates the format and length of generated comments.
- `generate_message(...)`: Generates a comment using the Llama model, with support for optional previous comment context.
- `image_to_text(image)`: Converts an image (PNG/JPG) to a descriptive caption using BLIP.
  
## 🖥️ Dependencies

- `transformers`
- `torch`
- `huggingface_hub`

Install requirements:
```bash
pip install transformers torch huggingface_hub
```

## 🔑 Setup

1. **Hugging Face Auth:**  
   Log in using your Hugging Face token:
   ```python
   from huggingface_hub import login
   login(token="YOUR_HF_TOKEN")
   ```

2. **Model Weights:**  
   - Text: `meta-llama/llama-3.2-3B-Instruct`
   - Image: `Salesforce/blip-image-captioning-base`

## ⚡ Usage Example

```python
result = generate_message(
    title="Mario Run",
    username_list=["player1", "player2", "player3"],
    description="Mario is running for life, help! ...",
    image_description=image_to_text("mario_test.png"),
    previous_comment="this game sucks im never playing it again"
)
print(result)
# Output example: player2: I actually love how fast-paced this looks! Makes me want to try it again.
```

## 📄 Function Overview

- `create_prompt(title, username_list, description, image_description, previous_comment=None)`
- `is_valid_message(message)`
- `generate_message(title, username_list, description, image_description, previous_comment=None)`
- `image_to_text(image)`

## 📝 Notes

- Modify the username list and style guidelines for your own use case.
- All comments are generated to be positive, playful, or constructively critical (no toxic output).
- Intended for research, prototyping, and fun social simulation.

---
MIT License (or specify your own)

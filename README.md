# Fabler

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A multimodal AI story teller, built with [Stable Diffusion](https://huggingface.co/spaces/stabilityai/stable-diffusion), GPT, and neural text-to-speech (TTS).

Given a prompt as an opening line of a story, GPT writes the rest of the plot; Stable Diffusion draws an image for each sentence; a TTS model narrates each line, resulting in a fully animated video of a short story, replete with audio and visuals.

![demo animation](https://user-images.githubusercontent.com/25360440/210071764-51ed5872-ba56-4ed0-919b-d9ce65110185.gif)


## Quickstart

### Install from [PyPi](https://pypi.org/project/fabler/)
```bash
$ pip install fabler
```


### Install from Source
1. Clone the repository

```bash
$ git clone https://github.com/christopherwoodall/fabler.git
```

2. Install package requirements.

```bash
$ pip install --upgrade pip wheel
$ pip install -e ".[developer]"
```

3. Run the demo. The final video will be saved as `/out/out.mp4`, alongside other intermediate images, audio files, and subtitles.

```bash
$ fabler --scene=scene.yaml
```

4 Alternatively with make:

```bash
make install && make run
```

## Usage

1. Load the model with defaults.

```python
from fabler import Fabler

story_teller = Fabler.from_defaults()
story_teller.generate(...)
```

2. Alternatively, configure the model with custom settings.

```python
from fabler import Fabler, FablerConfig

config = FablerConfig(
    writer="gpt2-large",
    painter="CompVis/stable-diffusion-v1-4",
    max_new_tokens=100,
    diffusion_prompt_prefix="Van Gogh style",
)

story_teller = Fabler(config)
story_teller.generate(...)
```

## License

Released under the [MIT License](LICENSE).

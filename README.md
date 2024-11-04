# 🌋 LLaVA Image tagger

thanks LLava

## Install

If you are not using Linux, do *NOT* proceed 

1. Clone this repository and navigate to LLaVA folder

```bash
git clone https://github.com/liushuchun/llava_image_tagger.git
cd llava_image_tagger
```

2. Install Package

```Shell
conda create -n llava python=3.10 -y
conda activate llava
pip install --upgrade pip  # enable PEP 660 support
pip install -e .
```

3. Install additional packages for training cases

```
pip install -e ".[train]"
pip install flash-attn --no-build-isolation
```

### Upgrade to latest code base

```Shell
git pull
pip install -e .

# if you see some import errors when you upgrade,
# please try running the command below (without #)
# pip install flash-attn --no-build-isolation --no-cache-dir
```

### Quick Start With HuggingFace

<details>
<summary>Example Code</summary>

```Python
from llava.model.builder import load_pretrained_model
from llava.mm_utils import get_model_name_from_path
from llava.eval.run_llava import eval_model

model_path = "liuhaotian/llava-v1.5-7b"

tokenizer, model, image_processor, context_len = load_pretrained_model(
    model_path=model_path,
    model_base=None,
    model_name=get_model_name_from_path(model_path)
)
```

Check out the details wth the `load_pretrained_model` function in `llava/model/builder.py`.

You can also use the `eval_model` function in `llava/eval/run_llava.py` to get the output easily. By doing so, you can use this code on Colab directly after downloading this repository.

```python
model_path = "liuhaotian/llava-v1.5-7b"
prompt = "What are the things I should be cautious about when I visit here?"
image_file = "https://llava-vl.github.io/static/images/view.jpg"

args = type('Args', (), {
    "model_path": model_path,
    "model_base": None,
    "model_name": get_model_name_from_path(model_path),
    "query": prompt,
    "conv_mode": None,
    "image_file": image_file,
    "sep": ",",
    "temperature": 0,
    "top_p": None,
    "num_beams": 1,
    "max_new_tokens": 512
})()

eval_model(args)
```

</details>

## LLaVA Weights

Please check out our [Model Zoo](https://github.com/haotian-liu/LLaVA/blob/main/docs/MODEL_ZOO.md) for all public LLaVA checkpoints, and the instructions of how to use the weights.

## Demo

### CLI Inference

```bash
python-mllava.serve.cli--model-path/media/shuchun/data/models/llava_v1.6--image-dir/media/shuchun/data --recursive--load-4bit--devicecuda
```

<style>#mermaid-1730724125342{font-family:sans-serif;font-size:16px;fill:#333;}#mermaid-1730724125342 .error-icon{fill:#552222;}#mermaid-1730724125342 .error-text{fill:#552222;stroke:#552222;}#mermaid-1730724125342 .edge-thickness-normal{stroke-width:2px;}#mermaid-1730724125342 .edge-thickness-thick{stroke-width:3.5px;}#mermaid-1730724125342 .edge-pattern-solid{stroke-dasharray:0;}#mermaid-1730724125342 .edge-pattern-dashed{stroke-dasharray:3;}#mermaid-1730724125342 .edge-pattern-dotted{stroke-dasharray:2;}#mermaid-1730724125342 .marker{fill:#333333;}#mermaid-1730724125342 .marker.cross{stroke:#333333;}#mermaid-1730724125342 svg{font-family:sans-serif;font-size:16px;}#mermaid-1730724125342 .label{font-family:sans-serif;color:#333;}#mermaid-1730724125342 .label text{fill:#333;}#mermaid-1730724125342 .node rect,#mermaid-1730724125342 .node circle,#mermaid-1730724125342 .node ellipse,#mermaid-1730724125342 .node polygon,#mermaid-1730724125342 .node path{fill:#ECECFF;stroke:#9370DB;stroke-width:1px;}#mermaid-1730724125342 .node .label{text-align:center;}#mermaid-1730724125342 .node.clickable{cursor:pointer;}#mermaid-1730724125342 .arrowheadPath{fill:#333333;}#mermaid-1730724125342 .edgePath .path{stroke:#333333;stroke-width:1.5px;}#mermaid-1730724125342 .flowchart-link{stroke:#333333;fill:none;}#mermaid-1730724125342 .edgeLabel{background-color:#e8e8e8;text-align:center;}#mermaid-1730724125342 .edgeLabel rect{opacity:0.5;background-color:#e8e8e8;fill:#e8e8e8;}#mermaid-1730724125342 .cluster rect{fill:#ffffde;stroke:#aaaa33;stroke-width:1px;}#mermaid-1730724125342 .cluster text{fill:#333;}#mermaid-1730724125342 div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:sans-serif;font-size:12px;background:hsl(80,100%,96.2745098039%);border:1px solid #aaaa33;border-radius:2px;pointer-events:none;z-index:100;}#mermaid-1730724125342:root{--mermaid-font-family:sans-serif;}#mermaid-1730724125342:root{--mermaid-alt-font-family:sans-serif;}#mermaid-1730724125342 flowchart-v2{fill:apa;}</style>

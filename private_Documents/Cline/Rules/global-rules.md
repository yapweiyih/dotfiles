## Documentation

- Give explanation on why you take the approach, best practise in a new markdown in `wy-tutorial` folder.
- The documentation will help reader to understand the approach.
- When creating function, always include input/output typing and doc string, example below:

```python
def get_product_information(product_id: str) -> dict:
    """
    Retrieves comprehensive information about a product based on the unique
    product ID.

    Args:
        product_id: The unique identifier for the product.

    Returns:
        A dictionary containing product details. Expected keys include:
        'product_name': The name of the product.
        'brand': The brand name of the product
        'description': A paragraph of text describing the product.
        'category': The category of the product.
        'status': The current status of the product (e.g., 'active',
        'inactive', 'suspended').

    Example return value:
        {
            'product_name': 'Astro Zoom Kid's Trainers',
            'brand': 'Cymbal Athletic Shoes',
            'description': '...',
            'category': 'Children's Shoes',
            'status': 'active'
        }
    """

    return {}
```

- When testing the python code, check if there is pyproject.toml, and use `uv run` method
- For each function that you create, you need to create pytest in `service_now/tests/tools` folder

## Agent framework ADK
- You can refer to llms.txt for the agent framework ADK sample code on how to create agent, subagent, tools, callback etc


## Command argument
- Use click python package.
- Example format as follows.

```python
@click.option(
    "--num-workers",
    type=int,
    default=1,
    help="Number of worker processes (default: 1)",
)
def deploy_agent_engine_app(
    num_workers: int,
) -> AgentEngine:
    """Deploy the agent engine app to Vertex AI."""

    logging.basicConfig(level=logging.INFO)
    logging.getLogger("httpx").setLevel(logging.WARNING)


    if "NUM_WORKERS" not in env_vars:
        env_vars["NUM_WORKERS"] = str(num_workers)


    print("""
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   🤖 DEPLOYING AGENT TO VERTEX AI AGENT ENGINE 🤖         ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
    """)

    # Log deployment parameters
    click.echo("\n📋 Deployment Parameters:")
    click.echo(f"  num_workers: {num_workers}")


if __name__ == "__main__":
    deploy_agent_engine_app()
```
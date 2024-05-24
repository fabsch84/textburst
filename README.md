# TextBurst

TextBurst is a  tool that facilitates automated creation of combinations from text parameters using lists of values and outputs them to a named pipe, allowing consumers to read them sequentially.

It's intented to generate a lot of configuration files to manage basic job execution. Each consumer process can read from the named pipe and will receive a new one for the next job.

## Example

**textburst.yaml** defines the possible values as lists. The keys match the placeholders in the template below.

```yaml
# set values for block1
block1: [1,2]

# set values for block2
block2: [3,4]

# set values for block3
block3: [5,6]
```

**config.yaml.j2** is the jinja2-style template where the single value combinations are inserted.

```yaml
block1:
    value: {{ block1 }}

block2:
    value: {{ block2 }}

block3:
    value: {{ block3 }}
```

Run **textburst** to populate a named pipe with each possible combination sequentially.

```bash
./textburst textburst.yaml config.yaml.j2 config_fifo &
```

Read from the named pipe to get each text individually.

```bash
cat < config_fifo
cat < config_fifo
cat < config_fifo
...
```
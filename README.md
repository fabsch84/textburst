# TextBurst

TextBurst is a  tool that facilitates automated creation of combinations from text parameters using lists of values and outputs them to a named pipe, allowing consumers to read them sequentially.

It's intented to generate a lot of configuration files to manage basic job execution. Each consumer process can read from the named pipe and will receive new ones for the next job.

# Directory and file manipulation

Check if dir exists and create it if not
```
if not os.path.exists(dir):
  os.makedirs(dir)
```

# Logging

Attach handler and output logging to a file
```
import logging

logger = logging.getLogger() # the global logger
# logger = logging.getLogger(__name__)
logger.setLevel(logging.INFO)

# create a file handler
handler = logging.FileHandler('hello.log')
handler.setLevel(logging.INFO)

# create a logging format
formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')
handler.setFormatter(formatter)

# add the handlers to the logger
logger.addHandler(handler)

logger.info('Hello baby')
```

+++
title = "Trying StackEdit as a WYSIWYG editor"
subtitle = ""

date = 2019-02-11
draft = false

authors = ["Gabi Udrescu"]

tags = []
+++

I just found out that [StackEdit](https://stackedit.io) has this feature that helps you write markdown in a WYSIWYG mode and allows you to commit files directly to GitHub. 

So, let's give it a spin:<!--more-->

**Bold text**
*Italic text*
## Big
# Bigger
~~Strikethrough~~

 - Bullet 1
 - Bullet 2
 - Bullet 3

 1. Numbered 1
 3. Numbered 2
 4. Numbered 3

Checklist

 - [ ] Task 1
 - [ ] Task 2
 - [x] (Checked) task 3


> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus nec
> nunc ullamcorper, auctor elit sit amet, porta lacus. Nam sit amet
> mauris mauris. Morbi a eros lorem. Morbi sollicitudin tempor leo, eget
> interdum risus. Proin arcu orci, imperdiet ac lorem ac, posuere
> pharetra est. Mauris et faucibus sapien. Pellentesque vel volutpat
> augue. Vestibulum ultrices scelerisque nisl mollis ultricies.

Code:

    <?php
	
	/*
	 * This file is part of the Symfony package.
	 *
	 * (c) Fabien Potencier <fabien@symfony.com>
	 *
	 * For the full copyright and license information, please view the LICENSE
	 * file that was distributed with this source code.
	 */

	namespace Symfony\Bundle\WebServerBundle;

	use Symfony\Component\Process\Exception\RuntimeException;
	use Symfony\Component\Process\PhpExecutableFinder;
	use Symfony\Component\Process\Process;

	/**
	 * Manages a local HTTP web server.
	 *
	 * @author Fabien Potencier <fabien@symfony.com>
	 */
	class WebServer
	{
	    const STARTED = 0;
	    const STOPPED = 1;

	    public function run(WebServerConfig $config, $disableOutput = true, callable $callback = null)
	    {
	        if ($this->isRunning()) {
	            throw new \RuntimeException(sprintf('A process is already listening on http://%s.', $config->getAddress()));
	        }

        $process = $this->createServerProcess($config);
        if ($disableOutput) {
            $process->disableOutput();
            $callback = null;
        } else {
            try {
                $process->setTty(true);
                $callback = null;
            } catch (RuntimeException $e) {
            }
        }

        $process->run($callback);

        if (!$process->isSuccessful()) {
            $error = 'Server terminated unexpectedly.';
            if ($process->isOutputDisabled()) {
                $error .= ' Run the command again with -v option for more details.';
            }

            throw new \RuntimeException($error);
        }
       }
[source](https://github.com/symfony/symfony/blob/master/src/Symfony/Bundle/WebServerBundle/WebServer.php)

Table:
|Key|Value|
|---|---|
|foo|bar|
|bar|foo|
|1|2|

  
| Command | Description |
| ------------------| ------------------------------ |
| `hugo` | Build your website. |
| `hugo serve -w` | View your website. |


![Predeal - I shot this awesome view](https://lh3.googleusercontent.com/DBA13JzpgFRsg6qdYv6z5oqnhHrSHIBWTZdYM7JduDHzPG4nOBuk9sx1NiaELx9xVW6lngskFD_D "Predeal - shot by me")

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjM1ODYwOTI5LDIwMzExOTQxNDMsLTIxMT
c0MTMwNTgsMTk3NjIzMTQzM119
-->
#!/usr/bin/env node
'use strict';

import fs from 'node:fs';
import path from 'node:path';
import util from 'node:util';
import svgstore from 'svgstore';

// Define the available command-line options
const argv_options = {
    inline: {
        short: 'i',
        type: 'boolean'
    },
    output: {
        short: 'o',
        type: 'string'
    },
    prefix: {
        short: 'p',
        type: 'string'
    }
};

// Parse the command-line arguments
const args = util.parseArgs({ strict: true, allowPositionals: true, options: argv_options });

const output = args.values.output;
const prefix = args.values.prefix;
const inline = args.values.inline;

// Make an array of all the inputs, expanding globs
const inputs = args.positionals.reduce(
    (total, files) => total.concat(fs.globSync(files)),
    []
);

if (inputs.length == 0) {
    console.error('No input files provided');
    process.exit(-1);
}

// Build up the spritesheet
const sprites = inputs.reduce(
    (sprites, file) => sprites.add(prefix + path.basename(file, '.svg'), fs.readFileSync(file, 'utf8')),
    svgstore({ inline: inline, renameDefs: true })
);

// Output to file, or to stdout
if (output) {
    fs.writeFileSync(output, sprites.toString({ inline: inline }));
} else {
    console.log(sprites.toString({ inline: inline }));
}

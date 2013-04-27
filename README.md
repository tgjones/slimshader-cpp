SlimShader
==========

SlimShader is a Direct3D shader bytecode parser for .NET and C++. This is the repository for the C++ version; the .NET version can be found at
[tgjones/slimshader](https://github.com/tgjones/slimshader).

Usage
-----

```cpp
auto fileBytes = ReadFileBytes("CompiledShader.o");
auto bytecodeContainer = DxbcContainer::Parse(fileBytes);

cout << bytecodeContainer.GetInputSignature()->GetParameters().size() << endl;
cout << bytecodeContainer.GetStatistics()->GetInstructionCount() << endl;
cout << bytecodeContainer.GetStatistics()->GetStaticFlowControlCount() << endl;
cout << bytecodeContainer.GetShader()->GetTokens().size() << endl;
```

Acknowledgements
----------------

* SlimShader uses several test shaders from the [HLSLCrossCompiler](https://github.com/James-Jones/HLSLCrossCompiler) project,
  by kind permission of [James Jones](https://github.com/James-Jones).
* The [Nuclex Framework](https://devel.nuclex.org/framework), in particular the 
  [HlslShaderReflector class](https://devel.nuclex.org/framework/browser/graphics/Nuclex.Graphics.Native/trunk/Source/Introspection/HlslShaderReflector.cpp),
  was very helpful when figuring out the RDEF, ISGN and OSGN chunks.
* The [Wine](https://github.com/mirrors/wine) project, in particular Wine's [shader reflection code](http://source.winehq.org/source/dlls/d3dcompiler_43/reflection.c),
  had some good tips for decoding the STAT chunk.
* [FXDIS](http://code.google.com/p/fxdis-d3d1x/) was useful to look at when getting started, but the techniques used
  in that project (casting raw bytes to struct types) don't translate well from C++ to C#.
* For the SHDR chunk, I mostly just used D3D11TokenizedProgramFormat.hpp, a header file that comes with the Windows DDK.

License
-------

SlimShader is released under the [MIT License](http://www.opensource.org/licenses/MIT).
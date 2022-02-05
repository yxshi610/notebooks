https://www.youtube.com/watch?v=W3gAzLwfIP0&list=PLlrATfBNZ98foTJPJ_Ev03o2oq3-GGOS2

#### Welcome to OpenGL

OpenGL: specification != library. No implementation codes. in Graphic drivers in binary form.

shader: program on GPU.

#### Setting up OpenGL and Creating a Window in C++

GLFW: open source, multi-platform library. simple API for creating windows, contexts and surfaces, receiving input and events.

```cpp
// old way. => should do glGenBuffers()
glBegin(GL_TRANGLES);
glVertex2f(-0.5f,-0.5f);
glVertex2f(0f,0.5f);
glVertex2f(0.5f,-0.5f);
glEnd();
```

#### Using Modern OpenGL in C++

GLEW: OpenGL Extension Wrangler Library. cross-platform open-source C/C++ extension loading library. provides efficient run-time mechanisms for determining which OpenGL extensions are supported. 

```cpp
// include before any others
#include GL/glew.h>
#include <GLFW/glfw3.h>

glfwMakeContextCurrent(window);
// Init after valid OpenGL context
if (glewInit() != GLEW_OK)
    std::cout << "GLEW ERROR!" << std::endl;
std::cout << glGetString(GL_VERSION) << std::endl;
```

#### Vertex Buffers + Vertex Attributes and Layouts + Shaders

vertex buffer: memory buffer. push bytes into it. in video ram.

- vertex shader
  
  - called for each vertex.
  
  - tell OpenGL vertex position.

- fragment shader (pixel)
  
  - run each for each pixel for rasterization.

- ...

```cpp

static unsigned int CompileShader(unsigned int type, const std::string& source) {}
    unsigned int id = glCreateShader(type);
    const char* src = source.c_str();
    glShaderSource(id, 1, &src, nullptr);
    glCompileShader(id);
    
    int result;
    glGetShaderiv(id, GL_COMPILE_STATUS, &result);
    if (result == GL_FALSE) {
        int length;
        glGetShaderiv(id, GL_INFO_LOG_LENGTH, &length);
        char* message = alloca(length * sizeof(char));
        glGetShaderInfoLog(id, length, &length, message);
        std::cout << "Failed to compile " << (type == GL_VERTEX_SHADER ? "vertex" : "fragment") << std::endl;
        std::cout << message << std::endl;
        glDeleteShader(id);
        return 0;
    }
        
    return id;
}

static unsigned int CreateShader(const std::string& vertex_shader, const std::string& freagment_shader) {
    unsigned int program = glCreateProgram();
    unsigned int vs = CompileShader(GL_VERTEX_SHADER, vertex_shader);
    unsigned int fs = CompileShader(GL_FRAGMENT_SHADER, fragment_shader);

    glAttachShader(program, vs);
    glAttachShader(program, fs);
    glLinkProgram(program);
    glValidateProgram(program);

    glDeleteShader(vs);
    glDeleteShader(fs);

    return program;
}


float positions[6] = {
    -0.5f, -0.5f,
     0.0f,  0.5f,
     0.5f, -0.5f
};
unsigned int buffer;
glGenBuffers(1, &buffer);
glBindBuffer(GL_ARRAY_BUFFER, buffer);
glBufferData(GL_ARRAY_BUFFER, 6 * sizeof(float), positions, GL_STATIC_DRAW);

glEnableVertexAttribArray(0);
// last two: stride, attribIndex.
glVertexAttribPointer(0, 2, GL_FLOAT, GL_FALSE, sizeof(float) * 2, 0);
std::string vertex_shader = 
    "#version 330 core\n"
    "\n"
    "layout(location = 0) in vec4 position;\n"
    "void main() {\n"
    "   gl_Position = position;\n"
    "}\n";

std::string fragment_shader = 
    "#version 330 core\n"
    "\n"
    "layout(location = 0) out vec4 color;\n"
    "void main() {\n"
    "   color = vec4(1.0, 0.0, 0.0, 1.0);\n"
    "}\n";

unsigned int shader = createShader(vertex_shader, fragment_shader);
glUseProgram(shader);

// in while
glDrawArrays(GL_TRANGLES, 0, 3);    // with binded one.


glDeleteProgram(shader);
```

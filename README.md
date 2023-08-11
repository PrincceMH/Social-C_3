# Social-C_3
# Sistema Social-C

## 1. Introducción

Este sistema está dirigido para el público en general que busca un acceso rápido y fluido al paquete de mensajería rápida. Además de compartir publicaciones, comentar y crear grupos de interés.

### 1.1. Propósito

El propósito de este documento es describir el comportamiento del Sistema Social-C definiendo las especificaciones funcionales y no funcionales. El documento incluye documentación de casos de uso textual que describen las interacciones entre el usuario y el administrador con el sistema.

### 1.2. Alcance

Con Social-C, una red social en plataforma móvil, los usuarios podrán interactuar mediante publicaciones, comentarios y un chat. Además, podrán modificar sus perfiles.

### 1.3 Definiciones, acrónimos y abreviaturas

- RF: Requisitos Funcionales
- RNF: Requisitos No Funcionales

### 1.4 Referencias

[IEEE. 2008. “Especificación de Requisitos según el estándar de IEEE 830”](https://www.fdi.ucm.es/profesor/gmendez/docs/is0809/ieee830.pdf)

## 2. Descripción general

En esta sección se presentan las características del sistema, incluyendo sus funcionalidades, agentes de uso y restricciones.

### 2.1. Perspectiva del producto

El sistema Social-C será implementado para ser navegado en una plataforma móvil, lo que permitirá un acceso y uso sencillos por parte del usuario.

### 2.2. Funcionalidad del producto

El sistema debe:

- Permitir chatear con otros participantes con el rol de usuario.
- Moderar las publicaciones y usuarios que infrinjan las reglas del sitio con el rol de administrador.
- Permitir almacenar y modificar publicaciones, comentarios y perfiles.
- Notificar al usuario sobre algún evento ocurrido en su cuenta (mensajes, publicaciones, anuncios del sistema).

### 2.3. Características de los usuarios

- **Administrador:** Encargado de moderar (prohibir, eliminar) publicaciones y usuarios.
- **Usuario:** Realizar cambios (publicar, comentar, editar, chatear) y navegar.

### 2.4. Restricciones

- Interfaz para ser usada con conexión a internet.
- El sistema se diseñará con arquitectura MVP (Model View Controller).
- Lenguajes y tecnologías: Android, Kotlin, Frameworks.
- Sistema de mensajería de Google Gmail.

### 2.5. Suposiciones y dependencias

- Se asume que los requisitos descritos son estables dentro del alcance del sistema.
- Los equipos en los que se ejecutará el sistema deben cumplir con los requisitos tecnológicos del sistema para su correcto funcionamiento.

## 3. Requisitos específicos
### 3.1. Requisitos Funcionales 

| Designación                | RF01                       |
|----------------------------|----------------------------|
| Nombre                     | Login                      |
| Prioridad                  | Alta                       |
| Descripción                | Permite iniciar sesión mediante un nombre de usuario y contraseña. |
| Acontecimiento desencadenante | El usuario desea interactuar con el sistema. |
| Actores                    | Usuario, Administrador     |
| Pre-condición              | El usuario/administrador debe estar registrado. |
| Post-condición             | Validar el login RF02.     |
| Resultado                  | Inicio de sesión en el sistema |
| Escenario principal        | El usuario/administrador ingresa su nombre de usuario y contraseña. El usuario/administrador valida su registro con un captcha. El sistema valida los datos ingresados. El usuario/administrador entra al sistema.|                          
| Escenario alternativo      | El usuario/administrador ingresa su nombre de usuario o contraseña incorrecta. 1a1.  El sistema notifica los datos incorrectos al usuario/administrador. El usuario/administrador no resuelve de manera correcta el captcha. 2a1.  El sistema notifica error de login. |
| Escenarios de excepción    | El usuario/administrador no ingresa ningún dato. |


| Designación                | RF03                       |
|----------------------------|----------------------------|
| Nombre                     | Registro                   |
| Prioridad                  | Alta                       |
| Descripción                | Permite al usuario registrar una cuenta. |
| Acontecimiento desencadenante | El usuario desea interactuar con el sistema. |
| Actores                    | Usuario                    |
| Pre-condición              | El usuario no tiene una cuenta. |
| Post-condición             | Validar registro RF04.     |
| Resultado                  | El usuario tiene una cuenta. |
| Escenario principal        | El usuario ingresa al registro. Se llenan los campos correspondientes. El sistema valida el registro. El usuario tiene una cuenta nueva. |
| Escenario alternativo      | El usuario completa de manera incorrecta los campos. 1a1. El sistema notifica error al llenar campos. El usuario ingresa un correo o número de teléfono inaccesibles. 2a1. El sistema no procesa el registro. |
| Escenarios de excepción    | El usuario completa los campos en blanco. |


| Designación                | RF05                       |
|----------------------------|----------------------------|
| Nombre                     | Chatear Usuario            |
| Prioridad                  | Alta                       |
| Descripción                | Permite interactuar directamente con uno o varios usuarios. |
| Acontecimiento desencadenante | El usuario desea interactuar con otro usuario en un chat. |
| Actores                    | Usuario                    |
| Pre-condición              | El permiso de chat entre usuarios concedido. |
| Post-condición             | Envío y recepción de mensajes. |
| Resultado                  | El usuario interactúa mediante mensajes con otro usuario. |
| Escenario principal        | El usuario selecciona el apartado de “chats”. El usuario selecciona el usuario para chatear. El sistema notifica el estado de conexión del otro usuario. El usuario envía un mensaje. |
| Escenario alternativo      | El sistema detecta que el permiso de chat entre usuarios no está concedido. 3a1. El sistema notifica los pasos para poder chatear. |
| Escenarios de excepción    | El usuario abandona el sistema. |


| Designación                | RF06                       |
|----------------------------|----------------------------|
| Nombre                     | Enviar y recibir mensaje   |
| Prioridad                  | Alta                       |
| Descripción                | Permite la comunicación directa de un usuario con otro a través del chat. |
| Acontecimiento desencadenante | El usuario desea iniciar una conversación/abrir chat. |
| Actores                    | Usuario                    |
| Pre-condición              | El permiso de chat entre usuarios concedido. Módulo de chat abierto.     |
| Post-condición             | Ninguna.                   |
| Resultado                  | El usuario interactúa mediante mensajes con otro usuario. |
| Escenario principal        | El usuario recibe el mensaje de otro usuario. El usuario envía el mensaje al otro usuario. El sistema verifica el envío y la llegada del mensaje. El otro usuario recibe el mensaje. |
| Escenario alternativo      | El sistema no detecta la llegada o el envío del mensaje. 3a1. El sistema notifica al usuario con “Error de envío/llegada” |
| Escenarios de excepción    | El usuario abandona el sistema. |



### 3.2. Requisitos No Funcionales 


| Designación           | RNF01                      |
|-----------------------|-----------------------------|
| Nombre                | Interfaz del sistema       |
| Prioridad             | Alta                        |
| Características       | El sistema presentará una interfaz de usuario sencilla, y con pocos elementos decorativos, para permitir una buena interacción entre usuario e interfaz. |
| Descripción           | La interfaz debe ser lo menos compleja posible. |


| Designación           | RNF02                      |
|-----------------------|-----------------------------|
| Nombre                | Compatibilidad             |
| Prioridad             | Alta                        |
| Características       | El sistema proporcionará un entorno adecuado para los distintos navegadores y dispositivos. |
| Descripción           | El sistema debe ser capaz de adaptarse a todo tipo de medio. |


| Designación           | RNF03                      |
|-----------------------|-----------------------------|
| Nombre                | Seguridad                  |
| Prioridad             | Alta                        |
| Características       | La seguridad del sistema se enfocará en proteger información crítica, valiosa o sensible para la organización. |
| Descripción           | El sistema garantiza seguridad con respecto a los datos del usuario que se impliquen en el sistema. |


| Designación           | RNF04                      |
|-----------------------|-----------------------------|
| Nombre                | Desempeño                  |
| Prioridad             | Alta                        |
| Características       | El sistema garantiza la interacción de los usuarios de manera eficiente. |
| Descripción           | El sistema debe almacenar las interacciones de los usuarios (publicaciones, comentarios, perfiles, chats) sin que afecte al tiempo de respuesta. |


# 4. Estilos de programación
### 4.1. Monolitic
Todo el proceso de registro dentro de un solo componente `Registro`. La interfaz de usuario, el manejo de eventos, la actualización de estados y la lógica de registro están contenidos en una sola entidad.

### 4.2. Hollywood
En este estilo, el flujo de control es manejado por una entidad central, y las partes del sistema son invocadas por esa entidad en respuesta a eventos o solicitudes.
En lugar de que un componente externo llame directamente a funciones en `Registro`, el flujo de control es controlado por React y los eventos, donde el componente `Registro` es "llamado" cuando se presenta el formulario o cuando se envía el registro.

```jsx
import { useContext } from "react";
import { Alert, Button, Form, Row, Col, Stack } from "react-bootstrap";
import { AutorContext } from "../context/AutorContext";

const Registro = () => {
    const {
        registerInfo,
        updateRegisterInfo,
        registerUser,
        registerError,
        isRegisterLoading,
    } = useContext(AutorContext);

    return (
        <>
            <Form onSubmit={registerUser}>
                <Row className="Formulario">
                    <Col xs={6}>
                        <Stack gap={3}>
                            <h2>Registro</h2>

                            <Form.Control
                                type="text"
                                placeholder="Nombre"
                                onChange={(e) =>
                                    updateRegisterInfo({
                                        ...registerInfo,
                                        name: e.target.value,
                                    })
                                }
                            />
                            <Form.Control
                                type="email"
                                placeholder="Email"
                                onChange={(e) =>
                                    updateRegisterInfo({
                                        ...registerInfo,
                                        email: e.target.value,
                                    })
                                }
                            />
                            <Form.Control
                                type="password"
                                placeholder="Contraseña"
                                onChange={(e) =>
                                    updateRegisterInfo({
                                        ...registerInfo,
                                        password: e.target.value,
                                    })
                                }
                            />
                            <Button variant="primary" type="submit">
                                {isRegisterLoading ? "Creando tu cuenta" : "Registro"}
                            </Button>
                            {registerError?.error && (
                                <Alert variant="danger">
                                    <p>{registerError?.message}</p>
                                </Alert>
                            )}

                        </Stack>
                    </Col>
                </Row>
            </Form>
        </>
    );
}

export default Registro;
```


### 4.3. Cookbook

Las funciones `createChat`, `findUserChats` y `findChat` pueden relacionarse con el estilo Cookbook en el sentido de que cada función aborda una tarea específica y bien definida. Cada función representa una "receta" para realizar una operación particular en la base de datos relacionados con los chats.
Cada función tiene una responsabilidad específica,createChat: Crea un nuevo chat entre dos usuarios,findUserChats: Encuentra todos los chats en los que un usuario específico es miembro,findChat: Encuentra un chat específico entre dos usuarios.


```jsx
const chatModel = require("../Models/chatModel");

// createChat
// findUserChats
// findChat

const createChat = async (req, res) => { 
    const { firstId, secondId } = req.body;

    try {
        const chat = await chatModel.findOne({ 
            members: { $all: [firstId, secondId] },
        });

        if (chat) return res.status (200).json(chat);

        const newChat = new chatModel({ 
            members: [firstId, secondId]
        })

        const response = await newChat.save();

        res.status(200).json(response);
    } catch (error) { 
        console.log(error);
        res.status(500).json(error);
    }
};

const findUserChats = async (req, res) => { 
    const userId = req.params.userId;

    try {
        const chats = await chatModel.find({ 
            members: { $in: [userId] },
    });

    res.status(200).json(chats);
    } catch (error) { 
        console.log(error); 
        res.status(500).json(error);
    }
};

const findChat = async (req, res) => {
    const {firstId, secondId} = req.params;
    try {
        const chat = await chatModel.findOne({
        members: { $all: [firstId, secondId] },
    });

    res.status(200).json(chat);    
    } catch (error) { 
        console.log(error);
        res.status(500).json(error); I
    }
};

module.exports = {createChat, findUserChats, findChat};
```


# 5. Principios SOLID
### 5.1 Principio de Responsabilidad Única
Cada función en este conjunto tiene una responsabilidad específica: createChat para crear un nuevo chat, findUserChats para buscar chats de un usuario y findChat para buscar un chat específico entre dos usuarios. Cumplen con este principio al abordar una sola tarea cada una.
const chatModel = require("../Models/chatModel");
createChat: Crea un nuevo chat entre dos usuarios.
findUserChats: Encuentra todos los chats en los que un usuario específico es miembro.
findChat: Encuentra un chat específico entre dos usuarios.

```
const createChat = async (req, res) => { 
    const { firstId, secondId } = req.body;

    try {
        const chat = await chatModel.findOne({ 
            members: { $all: [firstId, secondId] },
        });

        if (chat) return res.status (200).json(chat);

        const newChat = new chatModel({ 
            members: [firstId, secondId]
        })

        const response = await newChat.save();

        res.status(200).json(response);
    } catch (error) { 
        console.log(error);
        res.status(500).json(error);
    }
};

const findUserChats = async (req, res) => { 
    const userId = req.params.userId;

    try {
        const chats = await chatModel.find({ 
            members: { $in: [userId] },
    });

    res.status(200).json(chats);
    } catch (error) { 
        console.log(error); 
        res.status(500).json(error);
    }
};

const findChat = async (req, res) => {
    const {firstId, secondId} = req.params;
    try {
        const chat = await chatModel.findOne({
        members: { $all: [firstId, secondId] },
    });

    res.status(200).json(chat);    
    } catch (error) { 
        console.log(error);
        res.status(500).json(error); I
    }
};

module.exports = {createChat, findUserChats, findChat};
```
### 5.1 Principio de Abierto/Cerrado (OCP):
Cada función tiene una funcionalidad bien definida y no parece requerir modificaciones directas si se agregan nuevas funcionalidades relacionadas con la gestión de usuarios.
createToken(_id): Esta función toma un _id y genera un token JWT. Si en el futuro deseas agregar más información al token o modificar cómo se crea el token, puedes hacerlo en esta función sin cambiar el código que la utiliza.

registerUser(req, res): Esta función maneja el registro de un nuevo usuario. Si deseas agregar validaciones adicionales, procesos de autorización o algún otro comportamiento relacionado con el registro, puedes hacerlo en esta función sin afectar las otras partes del código.

loginUser(req, res): Esta función maneja la autenticación de un usuario. Si deseas agregar funcionalidades de autenticación como el uso de tokens de acceso, políticas de seguridad adicionales u otros métodos de autenticación, puedes hacerlo en esta función sin modificar el resto del código.

findUser(req, res): Esta función busca un usuario por su ID. Si en el futuro necesitas agregar más criterios de búsqueda o realizar operaciones adicionales en la búsqueda, puedes hacerlo aquí sin impactar otras partes del código.

getUsers(req, res): Esta función obtiene una lista de usuarios. Si deseas agregar paginación, filtros u otros métodos de obtención de usuarios, puedes hacerlo en esta función sin alterar las demás funciones.
```
const userModel = require("../Models/userModel");
const bcrypt = require("bcrypt");
const validator = require("validator");
const jwt = require("jsonwebtoken");

const createToken = (_id) => {
    const jwtkey = process.env.JWT_SECRET_KEY;

    return jwt.sign({_id}, jwtkey, {expiresIn: "3d"});
};

const registerUser = async (req, res) => {
    try{
        const {name, email, password} = req.body

        let user = await userModel.findOne({email});

        if(user) 
            return res.status(400).json("Este email ya está en uso...");

        if(!name || !email || !password) 
            return res.status(400).json("Todos los campos son obligatorios...");

        if(!validator.isEmail(email)) 
            return res.status(400).json("El email debe ser válido...");

        if(!validator.isStrongPassword(password))
            return res.status(400).json("La constraseña debe ser segura...");

        user = new userModel({name, email, password});

        const salt = await bcrypt.genSalt(10);
        user.password = await bcrypt.hash(user.password, salt);

        await user.save();

        const token = createToken(user._id);

        res.status(200).json({_id: user._id, name, email, token})
    }catch(error){
        console.log(error)
        res.status(500).json(error);
    }
};

const loginUser = async (req, res) => {
    const {email, password} = req.body;

    try{
        let user = await userModel.findOne({email});

        if(!user) return res.status(400).json("Email o contrasena invalidos...");

        const isValidPassword = await bcrypt.compare(password, user.password);

        if(!isValidPassword) 
            return res.status(400).json("Email o contrasena invalidos...");
        
        const token = createToken(user._id);

        res.status(200).json({_id: user._id, name: user.name, email, token})
    }catch(error){
        console.log(error)
        res.status(500).json(error);
    }
};

const findUser = async(req, res) => {
    const userId = req.params.userId;
    try{
        const user = await userModel.findById(userId);

        res.status(200).json(user);
    }catch(error){
        console.log(error)
        res.status(500).json(error);
    }
};

const getUsers = async(req, res) => {
    try{
        const user = await userModel.find();

        res.status(200).json(user);
    }catch(error){
        console.log(error)
        res.status(500).json(error);
    }
}

module.exports = {registerUser, loginUser, findUser, getUsers};
```
Trello: https://trello.com/b/pvwoTADC/social-c-is-i





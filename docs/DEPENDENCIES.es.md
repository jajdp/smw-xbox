# Dependencias

*(English: [DEPENDENCIES.md](DEPENDENCIES.md))*

## El proyecto del juego

| | |
|---|---|
| Repositorio | [snesrev/smw](https://github.com/snesrev/smw) |
| Commit | **`eae20c6`** — contra el que se generó el parche |
| Licencia | MIT (`LICENSE.txt`; GitHub no la detecta por el nombre del archivo) |

## Tu propia ROM

| | |
|---|---|
| Archivo | `Super Mario World (USA).sfc` |
| Tamaño | 524 288 bytes |
| SHA-256 | `0838e531fe22c077528febe14cb3ff7c492f1f5fa8de354192bdff7137c27f5b` |

Aquí no se distribuye nada de la ROM. El hash es una huella, para que puedas saber si tu volcado es
el que se usó para construir y probar esto.

## Herramientas de compilación

| | Qué hace falta | Por qué |
|---|---|---|
| Visual Studio 2022 | Con la **carga de trabajo de C++ para UWP** y el toolset **v143** | Aquí MSBuild compila, empaqueta *y* firma. Es la única familia de ports donde esa carga de trabajo es un requisito real |
| SDL2 | **2.26.3, en fuente**, vendorizado en `third_party\SDL2\` y retargeteado a v143 | Los binarios de escritorio no pueden correr en un AppContainer: sin backend de vídeo de WinRT y con importaciones que no están |
| SDK de Windows | 10.0.26100 o similar | Solo si reempaquetas con tus mosaicos (`makeappx`, `signtool`) |
| Python 3 | Cualquiera 3.8+ | `tools/apply_uwp.py`, solo biblioteca estándar; y la extracción de datos del propio proyecto |
| Una Xbox Series | En **modo desarrollador** y con un usuario conectado | Instalar un paquete sin nadie conectado parece un paquete roto |

## La consola

El `Microsoft.VCLibs.140.00` para x64 se instala junto al paquete como dependencia; no va dentro.
Viene con el SDK de Windows.

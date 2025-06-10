# ROS2
Trabalho de ROS2 para Disciplina de Introdução a Robótica

# Link para o video no YouTube
# https://youtube.com/shorts/-p8D8h1KyQc?si=eQsCDkq8eS3xrrCg

# Robot Controller Node

Este projeto implementa um nó ROS 2 responsável por controlar um robô através de uma sequência de waypoints predefinidos. O movimento envolve rotação e translação baseados em cálculos de orientação (yaw) e distância ao alvo.

## Pré-requisitos

- ROS 2 (recomenda-se a distribuição **Foxy**, **Galactic** ou superior)
- Python 3.8+
- Dependências ROS:
  - `rclpy`
  - `geometry_msgs`

## Estrutura do Projeto

```
robot_controller/
├── robot_controller_node.py
└── README.md
```

## Como Executar

1. **Crie um workspace ROS 2 (caso ainda não tenha):**

```bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
```

2. **Adicione o script ao seu workspace:**

Copie o arquivo `robot_controller_node.py` para a pasta `src` e crie um pacote:

```bash
ros2 pkg create --build-type ament_python robot_controller
cd robot_controller
mkdir robot_controller
mv ~/path/para/robot_controller_node.py robot_controller/
touch robot_controller/__init__.py
```

3. **Atualize o `setup.py`:**

```python
from setuptools import setup

package_name = 'robot_controller'

setup(
    name=package_name,
    version='0.0.0',
    packages=[package_name],
    install_requires=['setuptools'],
    zip_safe=True,
    maintainer='Seu Nome',
    maintainer_email='seu@email.com',
    description='Nó para controlar um robô via Twist e waypoints',
    license='MIT',
    entry_points={
        'console_scripts': [
            'robot_controller_node = robot_controller.robot_controller_node:main',
        ],
    },
)
```

4. **Construa o workspace:**

```bash
cd ~/ros2_ws
colcon build
source install/setup.bash
```

5. **Execute o nó:**

```bash
ros2 run robot_controller robot_controller_node
```

## Notas

- O robô deve estar escutando no tópico `/cmd_vel` do tipo `geometry_msgs/msg/Twist`.
- O sistema simula a movimentação do robô internamente, sem depender de sensores reais.

## Autor

Este projeto foi desenvolvido para fins acadêmicos e de simulação. Para mais informações, contate o autor do script.

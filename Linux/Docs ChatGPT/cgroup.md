Los **cgroups**, también conocidos como **control groups**, son un mecanismo en el kernel de Linux que permite limitar, priorizar y aislar el uso de recursos del sistema, como CPU, memoria, ancho de banda de red y dispositivos, entre diferentes grupos de procesos. Esto es útil para garantizar que ciertos procesos no consuman todos los recursos del sistema, lo que podría afectar negativamente a otros procesos y al rendimiento general del sistema.

Los cgroups son especialmente útiles en entornos donde se ejecutan múltiples aplicaciones o servicios en un mismo sistema, como servidores, máquinas virtuales o contenedores. Al usar cgroups, los administradores pueden asignar recursos de forma controlada a diferentes grupos de procesos, garantizando un uso eficiente y justo de los recursos del sistema.

Los cgroups ofrecen varias funcionalidades, incluyendo:

1.  **Limitación de Recursos:** Los cgroups permiten establecer límites en el uso de CPU, memoria, y otros recursos. Por ejemplo, puedes limitar la cantidad de CPU que un grupo de procesos puede utilizar para evitar que monopolice el procesador.
    
2.  **Priorización:** Los cgroups permiten establecer prioridades entre diferentes grupos de procesos. Los procesos en grupos con prioridad más alta tendrán acceso a los recursos antes que los procesos en grupos con prioridad más baja.
    
3.  **Control de Acceso a Dispositivos:** Los cgroups permiten restringir el acceso a dispositivos específicos para grupos de procesos. Esto es útil en entornos donde es necesario controlar qué procesos pueden acceder a ciertos dispositivos.
    
4.  **Aislamiento:** Los cgroups permiten aislar grupos de procesos unos de otros. Esto es especialmente importante en entornos de contenedores, donde se necesita asegurar que los procesos en un contenedor no afecten ni sean afectados por procesos en otros contenedores o en el sistema anfitrión.
    

Los cgroups son una herramienta fundamental en tecnologías de virtualización y contenedores, como Docker y Kubernetes, ya que permiten un control detallado y flexible sobre el uso de recursos de sistema en estos entornos. Además, los cgroups son gestionados y configurados mediante interfaces en el sistema de archivos `/sys/fs/cgroup` en sistemas Linux, lo que proporciona una forma conveniente de interactuar con ellos y configurar sus propiedades.
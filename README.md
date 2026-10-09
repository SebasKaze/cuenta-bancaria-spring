# Cajero automático — Spring Core e inyección de dependencias

**Autor:** Hilario Sebastian Espinoza Garcia

## Cómo correrlo

    ./correr.sh App final-app
    ./probar.sh final

## Las piezas

| Bean | Clase | Cómo lo declara Spring (`@Component` o `@Bean`) | Singleton o prototype |
|---|---|---|---|
| cajeroAutomatico | CajeroAutomatico | @Component | Singleton |
| repositorioEnMemoria | RepositorioEnMemoria | @Component | Singleton |
| antifraudePorMonto | AntifraudePorMonto | @Component | Singleton |
| reloj | java.time.Clock | @Bean | Singleton |

## Boleto de salida

1. ¿Qué es la inyección de dependencias? Explícalo con el cajero, en tus palabras.

Es el recibir por fuera los elementos que necesita en este caso el constructor. 

2. En la MP-1, ¿quién decidía qué antifraude usaba el cajero? ¿Y desde la MP-2?

Lo decidia el main, el cajero unicamente conoce la interfaz ServicioAntifraude. En MP-2 es @Bean quien le dice a Spring las piezas que se necesitan por medio de una inyeccion.

3. ¿Cuándo usarías `@Bean` en vez de `@Component`? Da el ejemplo de hoy.

Su uso es similar, ya que ofrecen un resultado parecido. @Bean lo ocuparia si quisiera tener el arbol de dependencias bajo control, en cambio, usar @Component deja que Spring busque automaticamente las clases y las inyecta lo cual delegas cierto trabajo como en el codigo de ConfiguracionBanco.java

4. ¿Qué gana: `@Primary` o `@Qualifier`? ¿Por qué tiene sentido?

@Qualifier gana porque es mas especifico al buscar por su nombre que por el de defecto

5. En tu proyecto de Empleados de la Semana 3 nunca escribiste `@ComponentScan`. ¿Quién lo hace? (Pista: abre la anotación `@SpringBootApplication` con `Ctrl+clic` y busca las anotaciones que tiene arriba.)

Quiero suponer que es @EnableAutoConfiguration. Revisa qué librerías tienes instaladas en el proyecto y autoconfigura automáticamente los Beans necesarios.

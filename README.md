<div align="center">
    <img src="https://centrodeconocimiento.agesic.gub.uy/o/agesic-cci-theme-nuevo/images/logo_presidencia.png" alt="logo" width="200" height="auto" /></br>
    <img src="https://centrodeconocimiento.agesic.gub.uy/o/agesic-cci-theme-nuevo/images/logo-agesic.svg" alt="logo" width="200" height="auto" />
    <h1>Theme - Panel de visualización CDE</h1>
</div>

<!-- Table of Contents -->
# Tabla de contenido
- Sobre el repositorio
  - Capturas de pantalla
  - Tecnologías
  - Características
  - Referencia de colores
- Como empezar
  - Prerrequisitos
  - Instalación del tema
  - Aplicar un tema
  - Configuración
    - General
    - Organismo
    - Layout
    - Links de interés
    - Información de contacto
    - Links relacionados
    - Idioma
  - Variables de entorno
- Uso
  - Estructuras pre-creadas
    - Paneles
    - Subpaneles
    - Filtros
    - Filtros de visualización
  - Sistema de grilla
  - Filtros de componentes
  - Filtros de página

## Sobre el repositorio
Se contienen los archivos necesarios para la creación de visualizadores interactivos de CDE, cumpliendo los estándares de diseño, interacción y accesibilidad pautados por el ente. El uso de este tema de Pentaho CDE asegura la representación uniforme de datos a través de toda la estructura de gobierno. 

<details>
  <summary>Tecnología</summary>
  <ul>
    <li><a href=https://developer.mozilla.org/es/docs/Web/JavaScript>Javascript</a></li>
    <li><a href=https://developer.mozilla.org/es/docs/Web/HTML>HTML</a></li>
    <li><a href=https://developer.mozilla.org/es/docs/Web/CSS>CSS</a></li>
    <li><a href="https://www.hitachivantara.com/en-us/products/pentaho-platform/data-integration-analytics.html">Pentaho</a></li>
  </ul>
</details>

**Versión 2.0**

# Como empezar

## Prerrequisitos

//Version de Pentaho Server

## Instalación del tema

Para instalar un tema y quede público para todos los futuros Dashboards CDE creados debemos subir el archivo **GubUY Theme V2.cdfde.zip** ubicado en este repositorio dentro de la carpeta **Public/cde/bootstrap**.

![](/Theme_CDE/7.png)

## Aplicar un tema
Todo nuevo Dashboard para una entidad del Gobierno Uruguayo debe realizarse aplicando la última versión del tema. 

1. Crear un nuevo Dashboard de tipo CDE
   
![](/Theme_CDE/1.png)

2. Ir a **Apply Template** en las acciones del menú del nuevo Dashboard.

![](/Theme_CDE/2.png)

3. Al realizar clic en dicha opción se desplegará una ventana emergente donde buscaremos el tema ***GubUY Theme V2*** bajo **MyTemplates**

![](/Theme_CDE/3.png)

4. Seleccionaremos el tema y haremoS clic en **Ok**

![](/Theme_CDE/4.png)

> [!IMPORTANT]
> La aplicación de un tema reemplaza todo el contenido ubicado en **Layout Panel** y **Components Panel**

![](/Theme_CDE/5.png)

Todo Dashboard CDE que cuente con el tema tendrá los siguientes archivos:
| Archivo | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| **Dashboard_ColorReferences** | `javascript` | Contiene objetos de color, o referencias de colores a ser utilizados en graficos. |
| **Dashboard_Scripts** | `javascript` | Documento que contiene funciones genéricas del Dashboard. Utilizado principalmente para la ejecución de filtros de página o AddIns genéricos del Dashboard.   |
| **Dashboard_CustomStyles** | `css` | Documento que contiene estilos custom para el Dashboard particular. Cualquier cosa que se considere genérica deberá ir en Theme_Agesic, teniendo en cuenta realizar una nueva publicación de la librería.  |
| **Lang_es** | `javascript` | Documento que contiene las variables de lenguaje para Español. |
| **Lang_en** | `javascript` | Documento que contiene las variables de lenguaje para Inglés.  |
| **Theme_Configs** | `javascript` | Documento que contine las configuraciones a realizar en el CDE sobre el cual estemos trabajando. |
| **Theme_DashboardDraw** | `javascript` | Documento que contiene los métodos y realiza los llamados para aplicar la configuración generada por el usuario dentro de CDE.(*) |
| **Theme_Agesic** | `css` | Documento que contiene los estilos del tema.(*) |
| **Favicon** | `javascript` |  |

> [!IMPORTANT]
> Cualquier modificación de los archivos marcados con * supone una nueva versión del tema.

También contendrá una estructura básica para comenzar a editar el panel.
1. **HTML – Header** Contiene la estructura del cabezal 
1. **HTML – MainContent** Contiene la estructura del cuerpo, filtros y contenido de pagina 
1. **HTML – Footer** Contiene la estructura del pie

![](/Theme_CDE/6.png)

Se añadirán también bajo **Components Panel** dos parámetros, los mismos deben ser incluidos como **listeners** de todo componente que los necesite para modificar su visualización. 
1. **param_lang** Encargado de comunicar el idioma que tiene activo el usuario
1. **param_mode** Encargado de comunicar el modo de visualización activo por el usuario (Light o Dark mode)


## Configuración

### General
**Generals**: Representa configuraciones generales del visualizador 

| Propiedad | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| **visualizador** | _`string`_ | Define y agrega el nombre del visualizador en los lugares correspondientes. |
| **langProperty** | _`string`_ | Define la propiedad que deben tener los elementos para que ejecute la traducción. |

### Organismo
**Organismo**: Representa el organismo responsable del visualizador 

| Propiedad | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| **urlorganismo** | _`string`_ | Define y agrega una URL de redirección al hacer click sobre el nombre del organismo. |
| **name** | _`string`_ | Define y agrega el nombre del organismo en los lugares correspondientes. | 
| **showTextOrganismo** | _`boolean`_ | Visualización del texto Organismo al lado del nombre. |
 
### Layout
**Pages**: Representa el listado de páginas/tabs que contendrá el layout, por cada ítem en su listado se creará un nuevo elemento de menú tanto en el header como en el footer. 

| Propiedad | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| **url** | _`string`_ | Define y setea una URL de redirección al hacer clic sobre el ítem del menú. En caso de ser un tab dentro del panel se debe dejar en null. | 
| **keyLang** | _`string`_ | Define el mapping key de traducción para el ítem del menú (Referencia al archivo de multi-idioma) |
| **id** | _`string`_ | Define y agrega un id al ítem de menú |
| **defaultActive** | _`boolean`_ | Define si el ítem es el que se tiene que mostrar activo por defecto. | 
| **targetContent** | _`string`_ | Define el contenido objetivo que va a visualizarse cuando se haga clic en el ítem de menú.  |
  
### Links de interés
**LowerLinks**: Representa los elementos de redirección visibles bajo el contenido de cada página.  

| Propiedad | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| **title[keyLang]** | _`string`_ | Define el mapping key de traducción para la propiedad título del ítem (Referencia al archivo de multi-idioma) | 
| **description[keyLang] o null** |  _`string`_ o _`null`_ | Define el mapping key de traducción para la propiedad descripción del ítem (Referencia al archivo de multi-idioma)  |
| **link** | _`string`_ | Define y agrega la url de redirección del ítem, no debería ir vacío  |
| **image** | _`string`_ o _`null`_ | Define y agrega la url de la imagen del ítem, puede no estar definido o ir en null | 

### Información de contacto
**Information**: Representa la información estática de contacto del organismo. 

| Propiedad | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| **address** | _`string`_ | Define y agrega la dirección del organismo  |
| **phone** | _`string`_ | Define y agrega el teléfono de contacto del organismo  |
| **working** | _`string`_ | Define y agrega las horas de atención del organismo  |
| **contact** | _`string`_ | Agrega una URL de contacto con el organismo  |

### Links relacionados
**Relacionados**: Representa los ítems de menú relacionados al panel. 

| Propiedad | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| **url** | _`string`_ | Define y agrega una URL de redirección al hacer clic sobre el ítem del menú de relacionados.  |
| **keyLang** | _`string`_ | Define el mapping key de traducción para el ítem del menú de relacionados (Referencia al archivo de multi-idioma)  |

### Idioma
**language**: Representa el listado de idiomas disponibles en el panel. Considerar que cada ítem en el listado debe incluir en el panel un recurso de tipo JS code snippet con su respectivo objeto de referencia.

| Propiedad | Tipo | Descripción |
| ------------- | ------------- | ------------- |
| **lang** | _`string`_ | Define el ISO para el idioma  |
| **text** | _`string`_ | Texto que indica el idioma  |
| **isDefault** | _`boolean`_ | Define y renderiza el idioma por defecto  |

 
# Uso

## Estructuras pre-creadas

### Paneles de visualización

![](/Theme_CDE/8.png)

```HTML
<div class="c-panel js-panel" id="idPanel"> 
  <header class="c-panel__header"> 
    <h3 class="c-panel__header-name is-blue">Titulo</h3> 
    <ul class="c-panel__header-actions"> 
      <li> 
        <button onclick="openModal('idModalFiltros')" class="is-filter"> 
          <i class="agesic-icon-filter material-symbols-rounded"></i>  
          <span>Filtros</span> 
        </button> 
      </li> 
      <li> 
        <button aria-label="Descargar datos" onclick="actionDownload('idPanel')" class="hideOnPrint"> 
          <i class="agesic-icon-download material-symbols-rounded"></i> 
        </button> 
      </li> 
    </ul> 
  </header> 
  <div class="c-panel__body"> 
      [CONTENIDO DEL PANEL] 
  </div> 
  <footer class="c-panel__footer"> 
    <i class="agesic-icon-info material-symbols-rounded"></i> 
    <p>Pie de seccion.</p> 
  </footer> 
</div> 
```
**Notas:**
1. Se puede cambiar el color de la barra del panel adicionando al elemento con clase `c-panel__header-name` una de las siguientes clases: 
`is-blue` `is-lightblue` `is-green` `is-red` `is-purple` 
1. Un panel puede contener **subpaneles** (Ver supaneles) pero no al revés. 
1. Se debe adicionar la clase `no-footer` a elemento con clase `.c-panel` en caso de no dibujar un pie de panel. 
1. Para las acciones de descarga del gráfico, se debe pasar un ID único en el método ***`actionDownload`***, en el ejemplo **idPanel**. Se descargará una única imagen de todo el contenido del panel.  
1. Para los filtros específicos del panel, se debe pasar un ID único en el método ***`openModal`***, en el ejemplo **idModalFiltros**, apuntando al modal que contiene los filtros específicos para dicho panel.  

### Subpaneles

![](/Theme_CDE/9.png)

```HTML
<div class="c-subpanel js-subpanel" id="idSubPanel">  
  <header class="c-subpanel__header">  
    <h4 class="c-subpanel__header-name">Título subpanel</h4>  
    <ul class="c-subpanel__header-actions">  
      <li>  
        <button aria-label="Descargar datos" onclick="actionDownload('idSubPanel')" class="hideOnPrint">  
          <i class="agesic-icon-download material-symbols-rounded"></i>  
        </button>  
      </li>  
    </ul>  
  </header>    
  <div class="c-subpanel__body">[CONTENIDO SUBPANEL]</div>  
  <footer class="c-subpanel__footer">  
    <i class="agesic-icon-info material-symbols-rounded"></i>  
    <p>Pie del subpanel</p> 
  </footer>  
</div>                             
```
**Notas:**
1. Un **subpanel** siempre está contenido por un **panel**. 
1. Se debe adicionar la clase `no-footer` a elemento con `.c-subpanel` en caso de no dibujar un pie de subpanel. 
1. Para las acciones de descarga del gráfico, se debe pasar un ID único en el método ***`actionDownload`***, en el ejemplo **idSubPanel**. Se descargará una única imagen de todo el contenido del panel. 


### Filtros (De panel y subpanel)

![](/Theme_CDE/11.png)

Todo panel `.c-panel` o subpanel `.c-subpanel` que contenga filtros específicos deberá contar con un elemento **div** de clase `c-panel__filters` y un ID único que lo identifique dentro del cuerpo respectivamente. 

 ```HTML
<div class="c-panel js-panel" id="idPanel"> 
  <header class="c-panel__header"> 
    <h3 class="c-panel__header-name is-blue">Titulo</h3> 
    <ul class="c-panel__header-actions"> 
      <li> 
        <button onclick="openModal('idModalFiltros')" class="is-filter"> 
          <i class="agesic-icon-filter material-symbols-rounded"></i>  
          <span>Filtros</span> 
        </button> 
      </li> 
      <li> 
        <button aria-label="Descargar datos" onclick="actionDownload('idPanel')" class="hideOnPrint"> 
          <i class="agesic-icon-download material-symbols-rounded"></i> 
        </button> 
      </li> 
    </ul> 
  </header> 
  <div class="c-panel__body">
      <div id="panelFilters" class="c-panel__filters"></div> 
      [CONTENIDO DEL PANEL] 
  </div> 
  <footer class="c-panel__footer"> 
    <i class="agesic-icon-info material-symbols-rounded"></i> 
    <p>Pie de seccion.</p> 
  </footer> 
</div> 
```

En dicho contenedor se dibujarán los distintos filtros seleccionados por el usuario, y podrá eliminar filtros previamente agregados.  

![](/Theme_CDE/12.png)

```HTML
<div role="dialog" id="idModalFiltros" aria-labelledby="idModalTitle" aria-modal="true"> 
  <button onclick="closeModal('idModalFiltros')" aria-label="Close"> 
    <i class="agesic-icon-close material-symbols-rounded"></i> 
  </button> 
  <h4 id="idModalTitle">Filtros</h4> 
  <div class="c-filters"> 
    <div class="c-form__group"> 
      <label for="render_idPentahoFilter">Filtro:</label> 
      <div id="idPentahoFilter" data-param="paramName" data-param-default="Filtro Aplicado" data-component-name="idPentahoFilter"></div> 
    </div> 
    <div class="c-modal__actions"> 
      <button class="c-button is-primary js-filterParameters" onclick="filterParameters('idModalFiltros', 'idPanelFilters', 'componentNameToUpdate')">Filtrar</button> 
      <button class="c-button is-secondary" onclick="closeModal('idModalFiltros')">Cancelar</button> 
    </div> 
  </div> 
</div>
```

| Referencia | Descripción |
| ------------- | ------------- |
| **idModalFilters** | ID correspondiente al modal, se usa abrir o cerrar el modal de filtros. |
| **idModalTitle** | ID correspondiente al título del modal, se usa para nombrar el modal |
| **render_idPentahoFilter** | ID del componente de filtro luego de dibujado por Pentaho |
| **idPentahoFilter** | ID del wrapper donde se va a dibujar el componente |
| **paramName** | Nombre del parámetro que modifica el filtro |
| **Filtro Aplicado** | Valor por defecto del selector |
| **componentNameToUpdate** | Nombre del componente que se va a ver afectado en caso de filtrar, se usa para llamar el update |
| **idPanelFilters** | ID del wrapper donde se dispondrán los filtros una vez filtrados, se usa para renderización  |

### Filtros por tipo visualización

![](/Theme_CDE/10.png)

Para aquellos gráficos que presenten más de un tipo de visualización posible, se podrá envolver el filtro de Radio dispuesto por la herramienta con un div de clase `c-visualizer`, modificando dicha presentación. 

## Sistema de grilla

El theme maneja un sistema de grilla de fácil adopción y manipulación utilizando css grid para su visualización en distintos dispositivos y tamaños. Su manejo se fundamenta en mobile first. 

```HTML
<div class="u-grid" grid-cols="12" grid-gap="4">
  <div grid-span="4">1 column of 3</div> 
  <div grid-span="4">1 column of 3</div> 
  <div grid-span="4">1 column of 3</div> 
</div> 
```

**Notas:**
1. El elemento con clase `u-grid`, define un contenedor de tipo grilla, aplicandole los estilos necesarios para hacer uso de CSS Grid. 
1. El elemento `u-grid`, define la cantidad de columnas a considerar mediante el agregado del atributo `grid-cols` y asignándole el valor deseado. Se usa un máximo de 12 columnas. 
1. Todo contenido hijo de el elemento `.u-grid` será tratado como una columna. 
1. El atributo `grid-gap`, define el espaciado entre las columnas en ambas direcciones. Se tiene la alternativa de utilizar `grid-gap-x` o `grid-gap-y` para manejar los espaciados de forma independiente tanto para horizontal o vertical. 
1. El atributo `grid-span` define la cantidad de columnas que va a ocupar el bloque.   


| Breakpoints  | ≥576px | ≥768px | ≥992px | ≥1200px | ≥1400px | 
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| **Ocupación de columnas**  | `grid-span` | `grid-span-sm` | `grid-span-md` | `grid-span-lg` | `grid-span-xl` | `grid-span-xxl` |
| **Espaciado**  | `grid-gap` | `grid-gap-sm` | `grid-gap-md` | `grid-gap-lg` | `grid-gap-xl` | `grid-gap-xxl` |
| **Espaciado vertical**  | `grid-gap-y` | `grid-gap-y-sm` | `grid-gap-y-md` | `grid-gap-y-lg` | `grid-gap-y-xl` | `grid-gap-y-xxl` |
| **Espaciado horizontal**  | `grid-gap-x` | `grid-gap-x-sm` | `grid-gap-x-md` | `grid-gap-x-lg` | `grid-gap-x-xl` | `grid-gap-x-xxl` |

**Ejemplo:**
```HTML
<div class="u-grid" grid-cols="12" grid-gap="4"> 
  <div grid-span="12">Div ocupa el 100% del contenido - 12 columnas</div> 
  <div grid-span="6">Div ocupa el 50% del contenido - 6 columnas</div> 
  <div grid-span="6">Div ocupa el 50% del contenido - 6 columnas</div> 
  <div grid-span="12" grid-span-sm="4" grid-span-md="6" grid-span-xl="4">Segun breakpoint: XS 12, SM 4, MD 6, XL 4</div> 
  <div grid-span="12" grid-span-sm="8" grid-span-md="6" grid-span-xl="8">Segun breakpoint: XS 12, SM 8, MD 6, XL 8</div> 
</div> 
```

## Filtros de página

Para filtrar los componentes de una página debemos tener en cuenta lo siguiente: 

1. Los componentes no deben escuchar a los componentes de filtro 
1. Se debe agregar update de los mismos al momento de realizar clic en el botón de filtrar. 
1. Agregar accesibilidad a los controles de filtro 

![](/Theme_CDE/13.png)

El botón aplicar filtros, es el encargado de comunicar al Dashboard que los parámetros cambiaron, de forma que todos los componentes que dependen de esos parámetros modifiquen su valor.  

Para ello, cada boton de cada página dentro del Dashboard tendrá un evento onClick el cual se encargará de buscar el valor de los filtros de la página, y disparar el cambio en el Dashboard.  

_Ej. El Dashboard tiene una página con filtros, su botón cuenta con un Id `"idFiltroBoton"` y dos componentes `"nombre_componente_1"` y `"nombre_componente_2"` que se actualizan con el cambio de parámetros de los filtros._ 

  
```JAVASCRIPT
document.getElementById('idFiltroBoton').addEventListener('click', function (e) { 
  var components = [ 
    'nombre_componente_1', 
    'nombre_componente_2', 
  ]; 

  components.forEach( component => { 
    dashboard.getComponentByName('render_' + component).update();  
  }); 
});  
```
 
**Accesibilidad a los controles de filtro** 

Para ambos casos además es necesario agregar en el método **PostExecution** del componente la siguiente función, la misma es encargada de agregar accesibilidad a los componentes de filtro. Permitiendo la vinculación entre nombre y campo del filtro.
  
```JAVASCRIPT
function posEx(){  
  convertControl(this); 
}  
```
La definición de la función está definida en las funciones del tema.

## Filtros de componente

Únicamente si el componente tiene un valor pre-cargado como filtro o si es necesario que tenga un valor se debe agregar el siguiente código en el método **postFetch** del QueryComponent: 
```JAVASCRIPT
function pFetch(data){ 
  ...     
  var defaultParameter = dashboard.getParameterValue('paramName');     

  if(data.resultset.length > 0){ 
    var filterWrapper = document.getElementById('IDsectionFilters'); 
    filterWrapper.innerHTML  = ''; 

    if(defaultParameter){ 
      var filter = document.createElement('button'); 
      var icon = document.createElement('i'); 
      var text = document.createElement('span'); 
      icon.classList.add('agesic-icon-close','material-symbols-rounded');                
      filter.appendChild(icon); 
      text.textContent = defaultParameter; 
      filter.setAttribute('data-param', defaultParameter); 
      filter.setAttribute('data-default-value', defaultParameter); 
      filter.appendChild(text); 
      filterWrapper.appendChild(filter); 
     
      filter.addEventListener('click', function(e){ 
          openModal('idFiltersModal')  
      }); 
    } 
    … 
  } 
}
```

---
title: Кэш схемы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8667c55eed6de6b2b3c76af2ef45a5357a254516
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115995"
---
# <a name="schema-cache"></a>Кэш схем
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Editor предоставляет кэш схем, расположенный в каталоге %InstallRoot%\Xml\Schemas. Кэш схем - общий для всех пользователей компьютера и включает стандартные XML-схемы, используемые для поддержки технологии IntelliSense и проверки правильности XML-документа.  

 Редактор XML может также находить схемы, расположенные в решении, схемы, указанные в **схемы** поле документа **свойства** окна и схем, идентифицируемый `xsi:schemaLocation` и `xsi:noNamespaceSchemaLocation`атрибуты.  

 В следующей таблице приведены схемы, установленные редактором XML Editor.  

|     имя_файла      |                                                      Описание                                                      |
|-------------------|-----------------------------------------------------------------------------------------------------------------------|
|    catalog.xsd    |             Схема для файлов каталога схем редактора XML. Сведения о каталоге схем см. ниже.             |
| DotNetConfig.xsd  |                 Схема для файлов Web.Config, «<http://schemas.microsoft.com/.NETConfiguration/v2.0>».                 |
|    msbuild.xsd    |              Схема для файлов марки MSBuild, "<http://schemas.microsoft.com/developer/msbuild/2003>«.              |
|    msdata.xsd     | Схема для XSD-аннотаций, добавленных классом <xref:System.Data.DataSet>, «urn:schemas-microsoft-com:xml-msdata». |
|     msxsl.xsd     |                  Схема для расширений блоков скриптов XSLT (Майкрософт), urn:schemas-microsoft-com:xslt.                   |
| SnippetFormat.xsd |                 Схема для файлов фрагментов кода XML. Например, см. %InstallDir%\VC#\Expansions.                 |
|    Soap1.1.xsd    |            Схема для Simple Object Access Protocol (SOAP) 1.1, http://schemas.xmlsoap.org/soap/envelope/.            |
|    Soap1.2.xsd    |                                     Схема для протокола SOAP 1.2.                                     |
| SiteMapSchema.xsd |            Схема для XML-файл карты веб-узла ASP.NET, "<http://schemas.microsoft.com/AspNet/SiteMap-File-1.0>«.             |
|     wsdl.xsd      |                    Схема для языка описания веб-служб, http://schemas.xmlsoap.org/wsdl/.                     |
|     xenc.xsd      |                            Схема для XML-шифрования http://www.w3.org/2000/09/xmldsig#.                             |
|     xhtml.xsd     |                                    Схема для XHTML http://www.w3.org/1999/xhtml.                                     |
|     xlink.xsd     |                                  Схема для XLink1.0, http://www.w3.org/1999/xlink.                                   |
|      xml.xsd      |              Схема, описывающая атрибуты XML: space и XML: lang, http://www.w3.org/XML/1998/namespace.               |
|    xmlsig.xsd     |                        Схема для цифровых подписей XML http://www.w3.org/2000/09/xmldsig#.                         |
|   xsdschema.xsd   |                            Схема, описывающая XSD, http://www.w3.org/2001/XMLSchema.                            |
|     xslt.xsd      |                           Схема для преобразований XML, http://www.w3.org/1999/XSL/Transform.                            |

## <a name="updating-schemas-in-the-cache"></a>Обновление схем в кэше  
 Редактор загружает каталог кэша схем во время загрузки пакета редактора XML и следит за появлением изменений во время работы. Если произошло добавление схемы, она автоматически загружается в находящийся в оперативной памяти индекс известных схем. Если схема была удалена, она автоматически удаляется из индекса в оперативной памяти. Если схема была обновлена, она автоматически обозначает кэш этой схемы в оперативной памяти как недействительный.  

> [!NOTE]
>  Поскольку каталог кэша схем является глобальным на компьютере, в него следует добавлять только стандартные схемы, полезные для всех проектов Visual Studio, которые могут создаваться на этом компьютере.  

 Редактор XML также поддерживает любое количество файлов каталога схем в каталоге кэша схем. Каталоги схем могут указывать на другие расположения схем, которые должны быть известны редактору. Файл catalog.xsd определяет формат файла каталога и включается в каталог кэша схем. Файл catalog.xml является каталогом по умолчанию и содержит ссылки на другие схемы в %InstallDir%. Ниже приведен пример файла catalog.xml:  

```  
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">  
  <Schema href="%InstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>  
  <Schema href="%InstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>  
  <Schema href="%InstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>  
</SchemaCatalog>  
```  

 Атрибут `href` может представлять собой путь к любому файлу или URL-адрес по протоколу HTTP, указывающий на схему. Путь к файлу может быть указан относительно документа каталога. Следующие переменные, разделенные знаками %%, распознаются редактором и разворачиваются в обозначение пути:  

- InstallDir  

- Система  

- ProgramFiles  

- Programs  

- CommonProgramFiles  

- ApplicationData  

- CommonApplicationData  

- LCID  

  Документ каталога может включать элемент `Catalog`, указывающий на другие каталоги. Можно использовать элемент `Catalog` для указания центрального каталога, совместно используемого группой сотрудников или всем предприятием, или сетевого каталога, используемого совместно с бизнес-партнерами. Атрибут `href` представляет собой путь к файлу или URL-адрес по протоколу HTTP, указывающий на другие каталоги. Ниже приведен пример элемента `Catalog`:  

```  
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>  
```  

 Каталог также может управлять связыванием схем с XML-документами с помощью специального элемента `Association`. Этот элемент связывает схемы без целевого пространства имен с определенным расширением имен файлов, что может быть полезно, так как XML Editor не выполняет автоматическое связывание схем, не содержащих атрибута `targetNamespace`. В следующем примере элемент `Association` связывает схему dotNetConfig со всеми файлами, имеющими расширение CONFIG:  

```  
<Association extension="config" schema="%InstallDir%/xml/schemas/dotNetConfig.xsd"/>  
```  

## <a name="localized-schemas"></a>Локализованные схемы  
 Зачастую в файле catalog.xml нет записей для локализованных схем. Можно добавить дополнительные записи в файл catalog.xml, указывающие на каталог локализованных схем.  

 В следующем примере создается новый элемент `Schema` с переменной %LCID%, указывающей на локализованную схему.  

```  
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"  
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>  
```  

## <a name="changing-the-location-of-the-schema-cache"></a>Изменение местоположения кэша схем  
 Можно настроить расположение кэша схем с помощью **Разное** страница "Параметры". Если имеется каталог с избранными схемами, можно настроить редактор на использование этих схем.  

> [!NOTE]
>  Это изменение влияет только на работу текущего пользователя Visual Studio.  

#### <a name="to-change-the-schema-cache-location"></a>Изменение расположения кэша схем  

1. Из **средства** меню, выберите **параметры**.  

2. Разверните **текстовый редактор**, разверните **XML**, а затем нажмите кнопку **Разное**.  

3. Нажмите кнопку **Обзор** кнопку **схемы** поля.  

4. Выберите папку для кэша схемы и нажмите кнопку **ОК**.  

#### <a name="to-add-another-directory-of-common-schemas"></a>Добавление еще одного каталога часто используемых схем  

1. Внесите изменения в файл catalog.xml в каталоге кэша схем редактора XML.  

2. Добавьте новый элемент `<Catalog href="…"/>`, указывающий на каталог дополнительных схем.  

3. Сохраните изменения.  

     Каталог будет автоматически перезагружен.  

## <a name="see-also"></a>См. также  
 [XML-редактор](../xml-tools/xml-editor.md)

---
title: Кэш схем редактора XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6bba01c55e6e71a55895b7ebd16bb3063ed5c1f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904888"
---
# <a name="schema-cache"></a>Кэш схем

XML Editor предоставляет кэш схем, расположенный в *%InstallRoot%\Xml\Schemas* каталога. Кэш схем - общий для всех пользователей компьютера и включает стандартные XML-схемы, используемые для поддержки технологии IntelliSense и проверки правильности XML-документа.

Редактор XML может также находить схемы, расположенные в решении, схемы, указанные в **схемы** поле документа **свойства** окна и схем, идентифицируемый `xsi:schemaLocation` и `xsi:noNamespaceSchemaLocation`атрибуты.

В следующей таблице приведены схемы, установленные редактором XML Editor.


| имя_файла | Описание |
|-| - |
| *Catalog.xsd* | Схема для файлов каталога схем редактора XML. Сведения о каталоге схем см. ниже. |
| *DotNetConfig.xsd* | Схема для файлов Web.Config, «<http://schemas.microsoft.com/.NETConfiguration/v2.0>». |
| *MSBuild.xsd* | Схема для файлов марки MSBuild, "<http://schemas.microsoft.com/developer/msbuild/2003>«. |
| *msdata.xsd* | Схема для XSD-аннотаций, добавленных классом <xref:System.Data.DataSet>, «urn:schemas-microsoft-com:xml-msdata». |
| *msxsl.xsd* | Схема для расширений блоков скриптов XSLT (Майкрософт), urn:schemas-microsoft-com:xslt. |
| *SnippetFormat.xsd* | Схема для файлов фрагментов кода XML. Примеры, см. в разделе *%InstallDir%\VC#\Expansions*. |
| *Soap1.1.xsd* | Схема для Simple Object Access Protocol (SOAP) 1.1, http://schemas.xmlsoap.org/soap/envelope/. |
| *Soap1.2.xsd* | Схема для протокола SOAP 1.2. |
| *SiteMapSchema.xsd* | Схема для XML-файл карты веб-узла ASP.NET, "<http://schemas.microsoft.com/AspNet/SiteMap-File-1.0>«. |
| *WSDL.xsd* | Схема для языка описания веб-служб, http://schemas.xmlsoap.org/wsdl/. |
| *xenc.xsd* | Схема для XML-шифрования http://www.w3.org/2000/09/xmldsig#. |
| *XHTML.xsd* | Схема для XHTML http://www.w3.org/1999/xhtml. |
| *xlink.xsd* | Схема для XLink1.0, http://www.w3.org/1999/xlink. |
| *XML.xsd* | Схема, описывающая атрибуты XML: space и XML: lang, http://www.w3.org/XML/1998/namespace. |
| *xmlsig.xsd* | Схема для цифровых подписей XML http://www.w3.org/2000/09/xmldsig#. |
| *XSDSchema.xsd* | Схема, описывающая XSD, http://www.w3.org/2001/XMLSchema. |
| *XSLT.xsd* | Схема для преобразований XML, http://www.w3.org/1999/XSL/Transform. |

## <a name="update-schemas-in-the-cache"></a>Обновление схемы в кэше
 Редактор загружает каталог кэша схем во время загрузки пакета редактора XML и следит за появлением изменений во время работы. Если произошло добавление схемы, она автоматически загружается в находящийся в оперативной памяти индекс известных схем. Если схема была удалена, она автоматически удаляется из индекса в оперативной памяти. Если схема была обновлена, она автоматически обозначает кэш этой схемы в оперативной памяти как недействительный.

> [!NOTE]
> Поскольку каталог кэша схем является глобальным на компьютере, в него следует добавлять только стандартные схемы, полезные для всех проектов Visual Studio, которые могут создаваться на этом компьютере.


 Редактор XML также поддерживает любое количество файлов каталога схем в каталоге кэша схем. Каталоги схем могут указывать на другие расположения схем, которые должны быть известны редактору. *Catalog.xsd* файла определяет формат файла каталога и включается в каталог кэша схем. *Catalog.xml* файл является каталогом по умолчанию и содержит ссылки на другие схемы в *% InstallDir %*. Ниже приведен выборки *catalog.xml* файла:

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%InstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%InstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%InstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

 Атрибут `href` может представлять собой путь к любому файлу или URL-адрес по протоколу HTTP, указывающий на схему. Путь к файлу может быть указан относительно документа каталога. Следующие переменные, разделенные знаками %%, распознаются редактором и разворачиваются в обозначение пути:

-   InstallDir

-   Система

-   ProgramFiles

-   Programs

-   CommonProgramFiles

-   ApplicationData

-   CommonApplicationData

-   Код языка

Документ каталога может включать элемент `Catalog`, указывающий на другие каталоги. Можно использовать элемент `Catalog` для указания центрального каталога, совместно используемого группой сотрудников или всем предприятием, или сетевого каталога, используемого совместно с бизнес-партнерами. Атрибут `href` представляет собой путь к файлу или URL-адрес по протоколу HTTP, указывающий на другие каталоги. Ниже приведен пример элемента `Catalog`:

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

 Каталог также может управлять связыванием схем с XML-документами с помощью специального элемента `Association`. Этот элемент связывает схемы без целевого пространства имен с определенным расширением имен файлов, что может быть полезно, так как XML Editor не выполняет автоматическое связывание схем, не содержащих атрибута `targetNamespace`. В следующем примере элемент `Association` связывает схему dotNetConfig со всеми файлами, имеющими расширение CONFIG:

```xml
<Association extension="config" schema="%InstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Локализованные схемы
 Во многих случаях *catalog.xml* файл не содержит записей для локализованных схем. Можно добавить дополнительные записи для *catalog.xml* файл, который указывала на каталог локализованных схем.

 В следующем примере создается новый элемент `Schema` с переменной %LCID%, указывающей на локализованную схему.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Изменить расположение кэша схемы

Можно настроить расположение кэша схем с помощью **Разное** страница "Параметры". Если имеется каталог с избранными схемами, можно настроить редактор на использование этих схем.

> [!NOTE]
> Это изменение влияет только на работу текущего пользователя Visual Studio.

### <a name="to-change-the-schema-cache-location"></a>Изменение расположения кэша схем

1.  Из **средства** меню, выберите **параметры**.

2.  Разверните **текстовый редактор**, разверните **XML**, а затем нажмите кнопку **Разное**.

3.  Нажмите кнопку **Обзор** кнопку **схемы** поля.

4.  Выберите папку для кэша схемы и нажмите кнопку **ОК**.

### <a name="to-add-another-directory-of-common-schemas"></a>Добавление еще одного каталога часто используемых схем

1.  Изменить *catalog.xml* файл в каталог кэша схем редактора XML.

2.  Добавьте новый элемент `<Catalog href="..."/>`, указывающий на каталог дополнительных схем.

3.  Сохраните изменения.

     Каталог будет автоматически перезагружен.

## <a name="see-also"></a>См. также

- [XML-редактор](../xml-tools/xml-editor.md)
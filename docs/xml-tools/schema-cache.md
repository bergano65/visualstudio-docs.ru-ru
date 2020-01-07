---
title: Кэш схемы редактора XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40781a5249d9b69df5f41f863f3d36ac6a119645
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592494"
---
# <a name="schema-cache"></a>Кэш схем

Редактор XML предоставляет кэш схемы, расположенный в каталоге *%всинсталлдир%\ксмл\счемас* . Кэш схемы является глобальным для всех пользователей компьютера и включает стандартные схемы XML, используемые для проверки IntelliSense и XML-документа.

Редактор XML может также находить схемы, расположенные в решении, схемы, указанные в поле **схемы** окна **свойства** документа, и схемы, определяемые атрибутами `xsi:schemaLocation` и `xsi:noNamespaceSchemaLocation`.

В следующей таблице описаны схемы, которые устанавливаются вместе с редактором XML.

| {2&gt;Имя_файла&lt;2} | Описание |
|-| - |
| *Catalog. xsd* | Схема для файлов каталога схем редактора XML. Сведения о каталоге схем см. ниже. |
| *Дотнетконфиг. xsd* | Схема для файлов Web. config, `http://schemas.microsoft.com/.NETConfiguration/v2.0`. |
| *MSBuild. xsd* | Схема для создания файлов MSBuild, `http://schemas.microsoft.com/developer/msbuild/2003`. |
| *msdata.xsd* | Схема для XSD-аннотаций, добавленных классом <xref:System.Data.DataSet>, «urn:schemas-microsoft-com:xml-msdata». |
| *msxsl. xsd* | Схема для расширений блоков скриптов XSLT (Майкрософт), urn:schemas-microsoft-com:xslt. |
| *Сниппетформат. xsd* | Схема для файлов фрагментов кода XML. Примеры см. в разделе *% VSInstallDir%VC#\ \експансионс*. |
| *SOAP 1.1. xsd* | Схема для протокола SOAP 1,1, `http://schemas.xmlsoap.org/soap/envelope/`. |
| *SOAP 1.2. xsd* | Схема для протокола SOAP 1.2. |
| *Ситемапсчема. xsd* | Схема для XML-файла ASP.NET Sitemap `http://schemas.microsoft.com/AspNet/SiteMap-File-1.0`. |
| *WSDL. xsd* | Схема для языка описания веб-службы, `http://schemas.xmlsoap.org/wsdl/`. |
| *ксенк. xsd* | Схема для XML-шифрования `http://www.w3.org/2000/09/xmldsig#`. |
| *XHTML. xsd* | Схема для `http://www.w3.org/1999/xhtml`XHTML. |
| *XLink. xsd* | Схема для XLink 1.0, `http://www.w3.org/1999/xlink`. |
| *XML. xsd* | Схема, описывающая атрибуты XML: Space и XML: lang, `http://www.w3.org/XML/1998/namespace`. |
| *ксмлсиг. xsd* | Схема для цифровых подписей XML `http://www.w3.org/2000/09/xmldsig#`. |
| *кссдсчема. xsd* | Схема, описывающая саму XSD-схему, `http://www.w3.org/2001/XMLSchema`. |
| *XSLT. xsd* | Схема для преобразований XML, `http://www.w3.org/1999/XSL/Transform`. |

## <a name="update-schemas-in-the-cache"></a>Обновление схем в кэше

Редактор загружает каталог кэша схем во время загрузки пакета редактора XML и следит за появлением изменений во время работы. Если произошло добавление схемы, она автоматически загружается в находящийся в оперативной памяти индекс известных схем. Если схема была удалена, она автоматически удаляется из индекса в оперативной памяти. Если схема была обновлена, она автоматически обозначает кэш этой схемы в оперативной памяти как недействительный.

> [!NOTE]
> Поскольку каталог кэша схем является глобальным на компьютере, в него следует добавлять только стандартные схемы, полезные для всех проектов Visual Studio, которые могут создаваться на этом компьютере.

Редактор XML также поддерживает любое количество файлов каталога схем в каталоге кэша схем. Каталоги схем могут указывать на другие расположения схем, которые должны быть известны редактору. Файл *Catalog. xsd* определяет формат файла каталога и включается в каталог кэша схемы. Файл *Catalog. XML* является каталогом по умолчанию и содержит ссылки на другие схемы в *% VSInstallDir%* . Ниже приведен пример выборки файла *Catalog. XML* :

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%VSInstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

Атрибут `href` может представлять собой путь к любому файлу или URL-адрес по протоколу HTTP, указывающий на схему. Путь к файлу может быть указан относительно документа каталога. Следующие переменные, разделенные%%, распознаются редактором и разворачиваются по пути:

- VSInstallDir

- System

- ProgramFiles

- Programs

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- Код языка

Документ каталога может включать элемент `Catalog`, указывающий на другие каталоги. Можно использовать элемент `Catalog` для указания центрального каталога, совместно используемого группой сотрудников или всем предприятием, или сетевого каталога, используемого совместно с бизнес-партнерами. Атрибут `href` представляет собой путь к файлу или URL-адрес по протоколу HTTP, указывающий на другие каталоги. Ниже приведен пример элемента `Catalog`:

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

Каталог также может управлять связыванием схем с XML-документами с помощью специального элемента `Association`. Этот элемент связывает схемы, не имеющие целевого пространства имен, с определенным расширением файла, что может быть полезно, так как редактор XML не выполняет автоматическую привязку схем, не имеющих атрибута `targetNamespace`. В следующем примере элемент `Association` связывает схему dotNetConfig со всеми файлами, имеющими расширение CONFIG:

```xml
<Association extension="config" schema="%VSInstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Локализованные схемы

Во многих случаях файл *Catalog. XML* не содержит записей для локализованных схем. В файл *Catalog. XML* можно добавить дополнительные записи, указывающие на каталог локализованной схемы.

В следующем примере создается новый элемент `Schema` с переменной %LCID%, указывающей на локализованную схему.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Изменение расположения кэша схемы

Расположение кэша схемы можно настроить с помощью страницы **Прочие** параметры. Если имеется каталог с избранными схемами, можно настроить редактор на использование этих схем.

> [!NOTE]
> Это изменение влияет только на работу текущего пользователя Visual Studio.

### <a name="to-change-the-schema-cache-location"></a>Изменение расположения кэша схем

1. В меню **Сервис** выберите **Параметры**.

2. Разверните **текстовый редактор**, разверните **XML**, а затем щелкните **Прочее**.

3. Нажмите кнопку **Обзор** в поле **схемы** .

4. Выберите папку для кэша схемы и нажмите кнопку **ОК**.

### <a name="to-add-another-directory-of-common-schemas"></a>Добавление еще одного каталога часто используемых схем

1. Измените файл *Catalog. XML* в каталоге кэша схемы редактора XML.

2. Добавьте новый элемент `<Catalog href="..."/>`, указывающий на каталог дополнительных схем.

3. Сохраните изменения.

   Каталог будет автоматически перезагружен.

## <a name="see-also"></a>См. также:

- [Редактор XML](../xml-tools/xml-editor.md)

---
title: Кэш схем в редакторе XML
description: Узнайте о кэше схем, предоставляемом редактором XML и содержащем стандартные XML-схемы, используемые для поддержки технологии IntelliSense и проверки правильности XML-документов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3562b7238f9721c4153af02cce594bfb9e134b0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841897"
---
# <a name="schema-cache"></a>Кэш схем

Редактор XML поддерживает кэш схем, расположенный в каталоге *%VSInstallDir%\xml\Schemas*. Этот кэш схем, общий для всех пользователей компьютера, содержит стандартные XML-схемы, используемые для поддержки технологии IntelliSense и проверки правильности XML-документов.

Редактор XML может также находить схемы, расположенные в решении, указанные в поле **Схемы** в окне **Свойства** в документе, и указанные в атрибутах `xsi:schemaLocation` и `xsi:noNamespaceSchemaLocation`.

В следующей таблице описываются схемы, которые устанавливаются вместе с редактором XML.

| имя_файла | Описание |
|-| - |
| *catalog.xsd* | Схема для файлов каталога схем редактора XML. Сведения о каталоге схем см. ниже. |
| *DotNetConfig.xsd* | Схема для файлов Web.Config, `http://schemas.microsoft.com/.NETConfiguration/v2.0`. |
| *msbuild.xsd* | Схема для файлов сборки MSBuild, `http://schemas.microsoft.com/developer/msbuild/2003`. |
| *msdata.xsd* | Схема для XSD-аннотаций, добавленных классом <xref:System.Data.DataSet>, «urn:schemas-microsoft-com:xml-msdata». |
| *msxsl.xsd* | Схема для расширений блоков скриптов XSLT (Майкрософт), urn:schemas-microsoft-com:xslt. |
| *SnippetFormat.xsd* | Схема для файлов фрагментов кода XML. Примеры: *%VSInstallDir%\VC#\Expansions*. |
| *Soap1.1.xsd* | Схема для протокола SOAP 1.1, `http://schemas.xmlsoap.org/soap/envelope/`. |
| *Soap1.2.xsd* | Схема для протокола SOAP 1.2. |
| *SiteMapSchema.xsd* | Схема для XML-файла карты сайта ASP.NET, `http://schemas.microsoft.com/AspNet/SiteMap-File-1.0`. |
| *wsdl.xsd* | Схема для языка WSDL, `http://schemas.xmlsoap.org/wsdl/`. |
| *xenc.xsd* | Схема для шифрования XML, `http://www.w3.org/2000/09/xmldsig#`. |
| *xhtml.xsd* | Схема для XHTML `http://www.w3.org/1999/xhtml`. |
| *xlink.xsd* | Схема для XLink1.0, `http://www.w3.org/1999/xlink`. |
| *xml.xsd* | Схема с описанием атрибутов xml:space и xml:lang, `http://www.w3.org/XML/1998/namespace`. |
| *xmlsig.xsd* | Схема для цифровых подписей XML, `http://www.w3.org/2000/09/xmldsig#`. |
| *xsdschema.xsd* | Схема с описанием XSD, `http://www.w3.org/2001/XMLSchema`. |
| *xslt.xsd* | Схема для преобразований XML, `http://www.w3.org/1999/XSL/Transform`. |

## <a name="update-schemas-in-the-cache"></a>Обновление схем в кэше

Редактор загружает каталог кэша схем во время загрузки пакета редактора XML и следит за появлением изменений во время работы. Если произошло добавление схемы, она автоматически загружается в находящийся в оперативной памяти индекс известных схем. Если схема была удалена, она автоматически удаляется из индекса в оперативной памяти. Если схема была обновлена, она автоматически обозначает кэш этой схемы в оперативной памяти как недействительный.

> [!NOTE]
> Поскольку каталог кэша схем является глобальным на компьютере, в него следует добавлять только стандартные схемы, полезные для всех проектов Visual Studio, которые могут создаваться на этом компьютере.

Редактор XML также поддерживает любое количество файлов каталога схем в каталоге кэша схем. Каталоги схем могут указывать на другие расположения схем, которые должны быть известны редактору. Файл *catalog.xsd* определяет формат файла каталога и включается в каталог кэша схем. Файл *catalog.xml* считается каталогом по умолчанию и содержит ссылки на другие схемы в папке *%VSInstallDir%* . Ниже приведен пример файла *catalog.xml*:

```xml
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%VSInstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%VSInstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

Атрибут `href` может представлять собой путь к любому файлу или URL-адрес по протоколу HTTP, указывающий на схему. Путь к файлу может быть указан относительно документа каталога. Следующие переменные, разделенные знаками %%, распознаются редактором и разворачиваются в значении пути:

- VSInstallDir

- Система

- ProgramFiles

- Programs

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- LCID

Документ каталога может включать элемент `Catalog`, указывающий на другие каталоги. Можно использовать элемент `Catalog` для указания центрального каталога, совместно используемого группой сотрудников или всем предприятием, или сетевого каталога, используемого совместно с бизнес-партнерами. Атрибут `href` представляет собой путь к файлу или URL-адрес по протоколу HTTP, указывающий на другие каталоги. Ниже приведен пример элемента `Catalog`:

```xml
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

Каталог также может управлять связыванием схем с XML-документами с помощью специального элемента `Association`. Этот элемент связывает схемы без целевого пространства имен с определенным расширением имен файлов, что может быть полезно, так как редактор XML не выполняет автоматическое связывание схем, не содержащих атрибута `targetNamespace`. В следующем примере элемент `Association` связывает схему dotNetConfig со всеми файлами, имеющими расширение CONFIG:

```xml
<Association extension="config" schema="%VSInstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Локализованные схемы

Зачастую в файле *catalog.xml* нет записей для локализованных схем. Можно добавить в файл *catalog.xml* дополнительные записи, указывающие на каталог локализованных схем.

В следующем примере создается новый элемент `Schema` с переменной %LCID%, указывающей на локализованную схему.

```xml
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="change-the-location-of-the-schema-cache"></a>Изменение расположения для кэша схем

Вы можете настроить расположение кэша схем на странице параметров **Разное**. Если имеется каталог с избранными схемами, можно настроить редактор на использование этих схем.

> [!NOTE]
> Это изменение влияет только на работу текущего пользователя Visual Studio.

### <a name="to-change-the-schema-cache-location"></a>Изменение расположения кэша схем

1. В меню **Сервис** выберите **Параметры**.

2. Разверните пункт **Текстовый редактор**, затем **XML**, и выберите пункт **Разное**.

3. Нажмите кнопку **Обзор** для поля **Схемы**.

4. Выберите папку для кэша схем и щелкните **ОК**.

### <a name="to-add-another-directory-of-common-schemas"></a>Добавление еще одного каталога часто используемых схем

1. Внесите изменения в файл *catalog.xml* в каталоге кэша схем для редактора XML.

2. Добавьте новый элемент `<Catalog href="..."/>`, указывающий на каталог дополнительных схем.

3. Сохраните изменения.

   Каталог будет автоматически перезагружен.

## <a name="see-also"></a>См. также

- [Редактор XML](../xml-tools/xml-editor.md)

---
title: Манифест из ресурсов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb853963cc5ca6fbe6080249daa8fcf9c08bf943
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707281"
---
# <a name="manifest-from-resources"></a>Manifest from Resources
Манифест от ресурсов инструмент консоль приложение, которое принимает список ресурсов изображения (.png или .xaml файлы) и генерирует файл .imagemanifest, который позволяет эти изображения, которые могут быть использованы с Visual Studio Image Service. Кроме того, этот инструмент можно использовать для добавления изображений в существующий .imagemanifest. Этот инструмент полезен для добавления высокопроизводительных и тематических поддержки изображений в расширение Visual Studio. Сгенерированный файл .imagemanifest должен быть включен и развернут как часть расширения Visual Studio (.vsix).

## <a name="how-to-use-the-tool"></a>Как использовать инструмент
 **Синтаксис**

 ManifestFromРесурсы /ресурсы:\<> Dir1; \<Img1>\</сборка: \<AssemblyName> Факультативное> Args

 **Аргументы**

||||
|-|-|-|
|**Имя переключателя**|**Примечания**|**Обязательные или необязательные**|
|/ресурсы|Список изображений или каталогов, делянимых заполколонией. Этот список должен всегда содержать полный список изображений, которые будут в манифесте. Если будет дан только частичный список, записи, не включенные, будут потеряны.<br /><br /> Если данный файл ресурса является полосой изображения, инструмент разделит его на отдельные изображения, прежде чем добавлять каждое изображение в манифест.<br /><br /> Если изображение является файлом .png, мы рекомендуем вам форматировать имя, как это, так что \<инструмент может заполнить правильные атрибуты для изображения: Имя>. \<Ширина>. \<Высота>.png.|Обязательно|
|/сборка|Название управляемой сборки (без включения расширения) или маршрут времени выполнения родной сборки, хостающая ресурсы (относительно местоположения времени выполнения манифеста).|Обязательно|
|/манифест|Имя, которое следует дать генерируемому файлу .imagemanifest. Это также может включать абсолютный или относительный путь для создания файла в другом месте. Имя по умолчанию совпадает с именем сборки.<br /><br /> По \<умолчанию: \\ Текущий\>каталог><сборки .imagemanifest|Необязательный|
|/guidName|Имя, чтобы дать символ GUID для всех изображений в генерируемых манифест.<br /><br /> По умолчанию: АктивыГид|Необязательный|
|/rootPath|Корневой путь, который необходимо устранить перед созданием управляемых УРИ ресурсов. (Этот флаг должен помочь в случаях, когда инструмент получает относительный путь URI неправильно, в результате чего ресурсы не загружаются.)<br /><br /> По \<умолчанию: текущая> каталога|Необязательный|
|/рекурсивный|Установка этого флага говорит инструменту, чтобы повторно искать любые каталоги в аргументе /ресурсов. Опропускание этого флага приведет к поиску каталогов только на верхнем уровне.|Необязательный|
|/IsNative|Установите этот флаг, когда аргумент сборки является путем для родной сборки. Опустите этот флаг, когда аргумент сборки — это название управляемой сборки. (См. раздел Примечания для получения дополнительной информации об этом флаге.)|Необязательный|
|/newGuids|Установка этого флага говорит инструменту, чтобы создать новое значение для символа GUID изображений вместо слияния одного из существующего манифеста.|Необязательный|
|/newIds|Установка этого флага говорит инструменту для создания новых значений символа идентификатора для каждого изображения вместо слияния значений из существующего манифеста.|Необязательный|
|/nologo|Установка этого флага останавливает печать информации о продукте и авторских правах.|Необязательный|
|/?|РаспечататьСправка информация.|Необязательный|
|/help|РаспечататьСправка информация.|Необязательный|

 **Примеры**

- ManifestFromРесурсы /ресурсы:D:'Изображения /сборка:My.Assembly.Name /isNative

- ManifestFromResources /ресурсы:D:'Images-Image1.png;D:'Images/Image1.xaml /assembly:My.Assembly.Name/manifest:MyImageManifest.imagemanifest

- ManifestFromResources /ресурсы:D:'Images/Image1.png;D:'Images/Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds

## <a name="notes"></a>Примечания

- Инструмент поддерживает только файлы .png и .xaml. Любые другие типы изображений или файлов будут проигнорированы. Предупреждение генерируется для всех неподдерживаемых типов, встречающихся при разборе ресурсов. Если при завершении разбора ресурсов при отсутствии поддерживаемых изображений будет найдено, будет сгенерирована ошибка

- Следуя предложенному формату для изображений .png, инструмент установит значение размера/измерения для .png к размеру, указанному форматом, даже если он отличается от фактического размера изображения.

- Формат ширины/высоты может быть опущен для изображений .png, но инструмент будет считывать фактическую ширину/высоту изображения и использовать их для значения размера/измерения изображения.

- Запуск этого инструмента на одной и той же полосе изображения несколько раз для одного и того же .imagemanifest приведет к дублированию манифеста записей, потому что инструмент пытается разделить полоску изображения на автономные изображения и добавить их в существующий манифест.

- Слияние (опуская /newGuids или /newIds) должно быть сделано только для инструментируемых манифестов. Манифесты, настроенные или сгенерированные другими средствами, могут быть объединены неправильно.

- Манифесты, генерируемые для сборок назаних, возможно, должны быть отредактированы вручную за поколением, чтобы символы идентификатора соответствовали идентификаторам ресурсов из файла .rc от родной сборки.

## <a name="sample-output"></a>Пример выходных данных
 **Простой манифест изображения**

 Манифест изображения будет похож на этот файл .xml:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImage" Value="0" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```

 **Манифест изображения для полосы изображения**

 Манифест изображения для полосы изображения будет похож на этот файл .xml:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15197 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <ID Name="MyImageStrip_0" Value="1" />
    <ID Name="MyImageStrip_1" Value="2" />
    <ID Name="MyImageStrip" Value="3" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">
      <Source Uri="$(Resources)/MyImageStrip_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">
      <Source Uri="$(Resources)/MyImageStrip_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>
  <ImageLists>
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />
    </ImageList>
  </ImageLists>
</ImageManifest>
```

 **Изображение манифест для родной сборки изображения ресурсов**

 Манифест изображения для родных изображений будет похож на этот файл .xml:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- This file was generated by the ManifestFromResources tool.-->
<!-- Version: 14.0.15198 -->
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">
  <Symbols>
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />
    <ID Name="MyImage1" Value="0" />
    <ID Name="MyImage2" Value="1" />
  </Symbols>
  <Images>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage1)" Type="PNG" />
      </Source>
    </Image>
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">
      <Source Uri="$(Resources)">
        <Size Value="16" />
        <NativeResource ID="$(MyImage2)" Type="PNG" />
      </Source>
    </Image>
  </Images>
  <ImageLists />
</ImageManifest>
```

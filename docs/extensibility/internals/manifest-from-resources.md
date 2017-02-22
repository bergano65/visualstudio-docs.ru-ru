---
title: "Манифеста из ресурсов | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Манифеста из ресурсов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Манифест из средства ресурсы — консольное приложение, которое принимает список ресурсов изображений \(файлы с расширением PNG или .xaml\) и создает файл .imagemanifest, позволяющий эти образы для использования со службой образов в Visual Studio. Кроме того это средство можно использовать Добавление изображений к существующей .imagemanifest. Это средство можно использовать для добавления поддержку высокого Разрешения и темы для изображений в расширение Visual Studio. Файл созданный .imagemanifest следует состава и развернут как часть расширения Visual Studio \(.vsix\).  
  
## Как использовать средство  
 **Синтаксис**  
  
 ManifestFromResources \/resources: \< Dir1 \>; \< Img1 \>\/Assembly: \< AssemblyName \>\< необязательные аргументы \>  
  
 **Аргументы**  
  
||||  
|-|-|-|  
|**Имя коммутатора**|**Примечания**|**Обязательный или необязательный**|  
|\/Resources|Разделенный точками с запятыми список изображений или каталоги. Этот список всегда должен содержать полный список изображений, которые будут в манифесте. Если дано неполный список записей, которые не включены, будут потеряны.<br /><br /> Если файл данного ресурса полосу изображений, средство разделяет его на отдельные изображения перед добавлением каждого subimage в манифесте.<br /><br /> Если изображения PNG\-файл, рекомендуется форматировать имя следующим образом, чтобы средство можно заполнить необходимыми атрибутами для изображения: \< имя \>. \< ширина \>. \< высота \> .png.|Обязательный|  
|\/ Assembly|Имя управляемой сборки \(не включая расширение\) или путь выполнения сборки в машинном коде, на котором размещается ресурсы \(относительно расположения выполнения манифеста\).|Обязательно|  
|\/ manifest|Имя созданного .imagemanifest файл. Это также могут быть абсолютный или относительный путь, чтобы создать файл в другом месте. Имя по умолчанию соответствует имени сборки.<br /><br /> По умолчанию: \< текущий каталог \> \\ \< сборка \> .imagemanifest|Необязательный|  
|\/guidName|Имя, присваиваемое символом GUID для всех образов в создаваемом манифесте.<br /><br /> По умолчанию: AssetsGuid|Необязательный|  
|\/rootPath|Корневой путь, который должен быть отброшены перед созданием управляемых ресурсов идентификаторы URI. \(Этот флаг — помочь в случаях, когда средство Возвращает относительный путь URI неправильной ресурсы, которые не удалось загрузить.\)<br /><br /> По умолчанию: \< текущий каталог \>|Необязательный|  
|\/ RECURSIVE|Установка этого флажка указывает, что для рекурсивного поиска каталогов в аргументе \/resources. Опустив этот флаг приведет только верхнего уровня поиска каталогов.|Необязательный|  
|\/isNative|Установите этот флаг, если аргумент сборки является путь для собственной сборки. Исключить этот флаг, если аргумент сборки — имя управляемой сборки. \(См. в подразделе "Примечания" Дополнительные сведения об этом флаг\).|Необязательный|  
|\/newGuids|Установка этого флажка указывает, что для создания нового значения для символа образы GUID вместо слияние из существующего манифеста.|Необязательный|  
|\/newIds|Установка этого флажка указывает, что для создания новых значений символов идентификатора для каждого изображения вместо объединения значений из существующего манифеста.|Необязательный|  
|\/nologo|Этот флаг установлен останавливает продукта и авторских правах сведения из печати.|Необязательный|  
|\/?|Распечатайте справочной информации.|Необязательный|  
|\/help|Распечатайте справочной информации.|Необязательный|  
  
 **Примеры**  
  
-   ManifestFromResources \/resources:D:\\Images \/assembly:My.Assembly.Name \/isNative  
  
-   ManifestFromResources \/resources:D:\\Images\\Image1.png;D:\\Images\\Image1.xaml \/assembly:My.Assembly.Name \/manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources \/resources:D:\\Images\\Image1.png;D:\\Images\\Image1.xaml \/assembly:My.Assembly.Name \/guidName:MyImages \/newGuids \/newIds  
  
## Примечания  
  
-   Средство поддерживает только файлы .xaml и .png. Другие типы изображение или файл будет игнорироваться. Предупреждение для всех неподдерживаемых типов обнаружения при синтаксическом анализе ресурсы. Не поддерживается изображений, обнаружены ли завершено средство синтаксического анализа ресурсы, будет сформирована ошибка  
  
-   Следуя предполагаемый формат для изображений в формате PNG, средство будет присвоено значение измерения размер .png размер указан формат, даже если оно отличается от фактического размера изображения.  
  
-   Можно опустить формат ширины и высоты для изображения в формате PNG, но средство прочтет фактическое изображение ширины или высоты и использовать их для значения измерения размера изображения.  
  
-   При запуске этого средства на полосе же изображение несколько раз для одного .imagemanifest приведет манифеста повторяющиеся записи, так как средство пытается разделить полосу изображения в автономные образы и добавлять их в существующий манифест.  
  
-   Слияние \(пропуск \/newGuids или \/newIds\) должна выполняться только для созданных средством манифестов. Не может правильно объединены манифестов, которые были настроены или созданный с помощью других средств.  
  
-   Манифесты, созданные для собственные сборки может потребоваться изменить вручную после создания вносить символы идентификатор соответствует идентификаторы из собственной сборки RC\-файла ресурсов.  
  
## Пример результатов выполнения  
 **Манифест простого образа**  
  
 Манифест изображение будет иметь вид этот XML\-файл:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15197 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" /> <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" /> <ID Name="MyImage" Value="0" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImage)"> <Source Uri="$(Resources)/Xaml/MyImage.xaml" /> <Source Uri="$(Resources)/Png/MyImage.16.16.png"> <Size Value="16" /> </Source> </Image> </Images> <ImageLists /> </ImageManifest>  
```  
  
 **Изображение манифест полосу изображений**  
  
 Манифест изображения для полосу изображений будет аналогичен этот XML\-файл:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15197 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" /> <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" /> <ID Name="MyImageStrip_0" Value="1" /> <ID Name="MyImageStrip_1" Value="2" /> <ID Name="MyImageStrip" Value="3" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)"> <Source Uri="$(Resources)/MyImageStrip_0.png"> <Size Value="16" /> </Source> </Image> <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)"> <Source Uri="$(Resources)/MyImageStrip_1.png"> <Size Value="16" /> </Source> </Image> </Images> <ImageLists> <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)"> <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" /> <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" /> </ImageList> </ImageLists> </ImageManifest>  
```  
  
 **Манифест образа для собственной сборки графические ресурсы**  
  
 Манифест образа для образов в машинном коде будет аналогичен этот XML\-файл:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?> <!-- This file was generated by the ManifestFromResources tool.--> <!-- Version: 14.0.15198 --> <ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014"> <Symbols> <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" /> <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" /> <ID Name="MyImage1" Value="0" /> <ID Name="MyImage2" Value="1" /> </Symbols> <Images> <Image Guid="$(AssetsGuid)" ID="$(MyImage1)"> <Source Uri="$(Resources)"> <Size Value="16" /> <NativeResource ID="$(MyImage1)" Type="PNG" /> </Source> </Image> <Image Guid="$(AssetsGuid)" ID="$(MyImage2)"> <Source Uri="$(Resources)"> <Size Value="16" /> <NativeResource ID="$(MyImage2)" Type="PNG" /> </Source> </Image> </Images> <ImageLists /> </ImageManifest>  
```
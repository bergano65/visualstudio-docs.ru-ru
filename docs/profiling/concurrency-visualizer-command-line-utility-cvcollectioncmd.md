---
title: Программа командной строки "Визуализатор параллелизма"
description: Служебная программа командной строки CVCollectionCmd.exe используется для сбора трассировок, которые можно просмотреть в визуализаторе параллелизма. Для работы с ней не требуется установка Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 47da8ae405dc24cad5bab4c98384ad5db5a97ef2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941181"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Служебная программа командной строки "Визуализатор параллелизма" (CVCollectionCmd)
С помощью служебной программы командной строки "Визуализатор параллелизма" (*CVCollectionCmd.exe*) можно собирать трассировки из командной строки, чтобы просматривать их в визуализаторе параллелизма для Visual Studio. Эти средства можно использовать на компьютерах без установленной среды Visual Studio.

> [!NOTE]
> Начиная с версии Visual Studio 2013 визуализатор параллелизма — это дополнительное расширение. (Ранее он входил в состав Visual Studio.) Скачать [средства сбора данных визуализатора параллелизма для Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) можно в Центре загрузки.

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Скачать программу командной строки "Визуализатор параллелизма"
 Чтобы скачать и установить служебную программу командной строки, перейдите на страницу [Средства сбора данных визуализатора параллелизма для Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) и следуйте инструкциям. По умолчанию *CVCollectionCmd.exe* устанавливается в папке %ProgramFiles%\Microsoft Concurrency Visualizer Collection Tools\ (%ProgramFiles(x86)%\Microsoft Concurrency Visualizer Collection Tools\ на компьютерах с архитектурой x64).

## <a name="collect-a-trace-with-cvcollectioncmd"></a>Сбор трассировок с помощью CVCollectionCmd
 Вы можете собирать трассировки, запустив приложение в CVCollectionCmd или приложив его к CVCollectionCmd. Возможные варианты см. в справочнике по командам ниже. Пример

```cmd
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data
```

## <a name="commands-and-parameters"></a>Команды и параметры
 Чтобы получить справку по командам и параметрам в программе командной строки, введите следующую команду:

 **CvCollectionCmd /?**

|Параметр|Описание|Параметры|Возвращаемые значения|
|------------|-----------------|----------------|-------------------|
|query|Указывает, можно ли начать сбор данных.|Отсутствуют|Значение 0, если можно начать сбор данных.<br /><br /> Значение 1, если сбор данных уже выполняется.<br /><br /> Значение 2, если сбор данных не выполняется, но один или несколько требуемых сеансов [ETW](/dotnet/framework/wcf/samples/etw-tracing) уже активированы.|
|Launch|Запуск указанного процесса в визуализаторе параллелизма.|Путь к исполняемому файлу.|Значение 0, если запуск выполнен успешно.<br /><br /> Значение 1, если запуск завершился ошибкой, так как не удалось запустить целевое приложение.<br /><br /> Значение 13, если запуск завершился ошибкой, так как у CVCollectionCmd недостаточно разрешений для записи данных в указанный выходной каталог.|
|Attach|Начинает сбор трассировки для всей системы. В противном случае присоединяется процесс, если он указан.|Отсутствует.|Значение 0, если присоединение выполнено успешно.<br /><br /> Значение 1, если присоединение завершилось с ошибкой, так как был указан недопустимый или неоднозначный процесс.<br /><br /> Значение 13, если присоединение завершилось ошибкой, так как у CVCollectionCmd недостаточно разрешений для записи данных в указанный выходной каталог.|
|Detach|Остановка сбора данных.|Отсутствует.|Значение 0, если отмена присоединения выполнено успешно.<br /><br /> Значение 1, если отмена присоединения завершилась ошибкой, так как сбор данных не выполняется.<br /><br /> Значение 2, если отмена присоединения завершилась ошибкой, так как не удалось остановить сбор данных.|
|Анализ|Анализ указанной трассировки.|Полный путь к файлу CVTrace.|Значение 0, если анализ выполнен успешно.<br /><br /> Значение 1, если анализ не удалось запустить, так как была указана трассировка для всей системы, но целевой процесс не был задан.<br /><br /> Значение 2, если анализ не удалось запустить, так как не была указана трассировка для всей системы, но был задан целевой процесс.<br /><br /> Значение 3, если анализ завершился с ошибкой, так как был указан недопустимый процесс.<br /><br /> Значение 4, если анализ завершился с ошибкой, так как был указан недопустимый файл CVTrace.|
|LaunchArgs|Указывает аргументы целевого исполняемого файла. Этот параметр применяется только к команде Launch.|Аргументы командной строки для приложения.|Отсутствует.|
|Outdir|Указывает каталог, в котором сохраняются файлы трассировки. Применяется к командам Launch и Attach.|Путь каталога или относительный путь.|Отсутствует.|
|Процесс|Указывает процесс, присоединяемый при выполнении команды Attach, или процесс в анализируемой трассировке при выполнении команды Analyze. Применяется к командам Attach и Analyze.|PID или имя процесса.|Отсутствует.|
|Config|Указывает путь файла конфигурации, если требуется собирать нестандартные параметры.   Применяется к командам Launch, Attach и Analyze.|Путь каталога или относительный путь XML-файла конфигурации.|Отсутствует.|

## <a name="customize-configuration-settings"></a>Настройка параметров конфигурации
 Если вы используете CVCollectionCmd для сбора трассировок и хотите настроить параметры сбора данных, укажите их в файле конфигурации.

> [!NOTE]
> Если вы используете Visual Studio для сбора трассировок, не изменяйте файл конфигурации напрямую.  Вместо этого воспользуйтесь диалоговым окном [Дополнительные параметры](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) .

 Чтобы изменить параметры сбора, создайте файл конфигурации на компьютере, где будет выполняться программа CVCollectionCmd. Вы можете создать файл конфигурации с нуля или скопировать файл конфигурации с компьютера, на котором установлена среда Visual Studio, и изменить его. Имя файла — *UserConfig.xml*, он расположен в папке *Local AppData*. При запуске программы используйте параметр Config вместе с командами Launch, Attach или Analyze.  В параметре, связанном с параметром Config, укажите путь к файлу конфигурации.

### <a name="configuration-file-tags"></a>Теги файла конфигурации
 Файл конфигурации использует формат XML. Ниже приведены допустимые теги и значения.

| Тег | Описание | Значения |
|-------------------------| - | - |
| Config | Обозначает файл конфигурации в целом. | Должен содержать эти элементы:<br /><br /> MinorVersion<br />MajorVersion |
| MajorVersion | Задает основную версию файла конфигурации. | Для проектов [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] значение равно 1. Если значение не равно 1, служебная программа не будет работать. |
| MinorVersion | Задает дополнительную версию файла конфигурации. | Для проектов [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] значение равно 0. Если значение не равно 0, служебная программа не будет работать. |
| IncludeEnvSymbolPath | Задает значение, определяющее, используется ли символьный путь к среде (_NT_SYMBOL_PATH). | True<br />False |
| DeleteEtlsAfterAnalysis | Задает значение, которое определяет, удаляются ли ETL-файлы после завершения анализа. | True<br />False |
| SymbolPath | Указывает путь к серверу символов. Более подробную информацию см. в разделе [Получение файлов символов отладки с сервера символов Microsoft](/windows/win32/dxtecharts/debugging-with-symbols). | Имя каталога или URL-адрес. |
| Markers | Содержит список поставщиков маркеров. | Может быть пустым или содержать элементы MarkerProvider. |
| MarkerProvider | Указывает одного поставщика маркеров. | Должен содержать эти элементы:<br /><br /> Level<br />GUID<br />Name<br /><br /> Может содержать эти элементы:<br /><br /> Categories<br />IsEnabled |
| Уровень | Задает уровень важности MarkerProvider. | Низкий<br />Обычный<br />Высокий<br />Критический<br />Все |
| Guid | Глобальный уникальный идентификатор поставщика маркеров ETW. | Идентификатор GUID. |
| name | Задает описание поставщика маркеров. | Строка. |
| Категории | Задает категории, собираемые для поставщика маркеров. | Строка чисел или диапазонов чисел, разделенных запятой. |
| IsEnabled | Задает значение, которое определяет, включен ли поставщик маркеров для сбора данных. | True<br />False |
| FilterConfig | Указывает список параметров конфигурации событий ETW, которые фильтруются при сборе. | Может содержать эти элементы:<br /><br /> CollectClrEvents<br />ClrCollectionOptions<br />CollectSampleEvents<br />CollectGpuEvents<br />CollectFileIO |
| CollectClrEvents | Указывает значение, которое определяет, собираются ли события CLR. | True<br />False |
| ClrCollectionOptions | Указывает, будут ли собираться события CLR для неуправляемых приложений и события завершения NGEN. | Может содержать одно или оба из следующих значений или может быть пустым:<br /><br /> CollectForNative<br />DisableNGenRundown |
| CollectSampleEvents | Указывает значение, которое определяет, собираются ли примеры событий. | True<br />False |
| CollectGpuEvents | Указывает значение, которое определяет, собираются ли события, созданные DX. | True<br />False |
| CollectFileIO | Указывает значение, которое определяет, собираются ли события файлового ввода-вывода. | True<br />False |
| UserBufferSettings | Указывает список параметров пользовательского буфера. | Должен содержать эти элементы:<br /><br /> BufferFlushTimer<br />BufferSize<br />MinimumBuffers<br />MaximumBuffers |
| KernelBufferSettings | Указывает список параметров буфера ядра. | Должен содержать эти элементы:<br /><br /> BufferFlushTimer<br />BufferSize<br />MinimumBuffers<br />MaximumBuffers |
| BufferFlushTimer | Задает таймер сброса для буферов ETW. | Положительное целое число. |
| BufferSize | Объем памяти, выделенный для каждого буфера сеанса трассировки событий, в килобайтах. | Число от 0 до 1024. |
| MinimumBuffers | Минимальное число буферов, выделенных для пула буферов сеанса трассировки событий. | Положительное целое число, которое больше или равно числу логических ядер, умноженному на два. |
| MaximumBuffers | Максимальное число буферов, выделенных для пула буферов сеанса трассировки событий. | Число, которое больше или равно значению MinimumBuffers. |
| JustMyCode | Указывает список каталогов режима "Только мой код". | Список из элементов MyCodeDirectory, может быть пустым. |
| MyCodeDirectory | Указывает каталог, содержащий ваш код. | Абсолютный путь. |

### <a name="example"></a>Пример
 Вместо создания файла конфигурации с нуля можно скопировать следующий пример и изменить его в соответствии с вашими требованиями.

```xml
<?xml version="1.0"?>
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">

  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>

  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>

  <TraceLocation>C:\traces</TraceLocation>

  <SymbolPath>http://symweb</SymbolPath>

  <Markers>
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />

    <!-- The IsEnabled and Categories elements are optional -->
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />
  </Markers>

  <FilterConfig>
    <CollectClrEvents>true</CollectClrEvents>
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>
    <CollectSampleEvents>true</CollectSampleEvents>
    <CollectGpuEvents>true</CollectGpuEvents>
    <CollectFileIO>true</CollectFileIO>
  </FilterConfig>

  <UserBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </UserBufferSettings>

  <KernelBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </KernelBufferSettings>

  <!-- List of MyCodeDirectory directories -->
  <JustMyCode>
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>
  </JustMyCode>
</LocalConfig>

```

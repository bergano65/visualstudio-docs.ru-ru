---
title: Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6b0f72a4-70ca-4e55-b236-2ea1034fd8a7
caps.latest.revision: 32
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4852dc5b65f00f7d298f5f1a15d39ff041022578
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791996"
---
# <a name="extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel"></a>Расширение закодированных тестов пользовательского интерфейса и записей действий для поддержки Microsoft Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Платформа тестирования для закодированных пользовательских интерфейсов и записей действий поддерживает не все пользовательские интерфейсы. Возможно, пользовательский интерфейс, который вы хотите протестировать, не поддерживается. Например, невозможно напрямую создать закодированный тест пользовательского интерфейса или запись действия для электронной таблицы [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Тем не менее можно создать собственное расширение для платформы закодированных тестов пользовательского интерфейса, которое будет поддерживать определенный пользовательский интерфейс, используя расширяемость такой платформы. В следующем разделе представлен пример расширения платформы для поддержки создания закодированных тестов пользовательского интерфейса и записей действий для [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]. Дополнительные сведения о поддерживаемых платформах см. в статье [Поддерживаемые конфигурации и платформы для закодированных тестов пользовательского интерфейса и записей действий](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).  
  
 **Требования**  
  
- Visual Studio Enterprise  
  
  В этом разделе представлено расширение закодированного теста пользовательского интерфейса, которое может записывать и воспроизводить тесты листов Excel. В этом разделе и в комментариях к коду рассматривается каждая часть расширения для разработчиков, которые хотят создать такое расширение.  
  
  ![Архитектура тестов пользовательского интерфейса](../test/media/ui-testarch.png "UI_TestArch")  
  Общие сведения об архитектуре  
  
## <a name="download-the-sample"></a>Загрузка примера  
 Этот пример состоит из четырех проектов в решении `CodedUIExtensibilitySample.sln`:  
  
- CodedUIextensibilitySample;  
  
- ExcelCodedUIAddInHelper;  
  
- ExcelUICommunicationHelper;  
  
- SampleTestProject.  
  
  Скачайте образец из этой [записи блога](http://go.microsoft.com/fwlink/?LinkID=185592).  
  
> [!NOTE]
>  Образец предназначен для использования с Microsoft Excel 2010. Пример может работать с другими версиями Microsoft Excel, но в настоящее время это не поддерживается.  
  
## <a name="details-about-the-sample"></a>Сведения о примере  
 В следующих разделах приведены сведения о примере и его структуре.  
  
### <a name="microsoft-excel-add-in-excelcodeduiaddinhelper"></a>Microsoft Excel Add-in: ExcelCodedUIAddInHelper;  
 Этот проект включает надстройку, которая выполняется в процессе Excel. Краткие сведения о проекте надстройки см. в статье [Пример надстройки Excel для закодированного тестирования пользовательского интерфейса](../test/sample-excel-add-in-for-coded-ui-testing.md).  
  
 Дополнительные сведения см. в статье [Walkthrough: Creating Your First VSTO Add-in for Excel](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f) (Пошаговое руководство. Создание первой надстройки уровня приложения для Excel).  
  
### <a name="excel-ui-communication-exceluicommunicationhelper"></a>Взаимодействие пользовательского интерфейса Excel. ExcelUICommunicationHelper;  
 В этот проект входит `IExcelUICommunication` интерфейс и классы информации, которые используются для передачи данных между платформой закодированных тестов пользовательского интерфейса и Excel. Дополнительные сведения см. в статье [Sample Excel Communicator Interface](../test/sample-excel-communicator-interface.md) (Пример интерфейса Excel Communicator).  
  
### <a name="coded-ui-test-extension-codeduiexentsibilitysample"></a>Расширение закодированных тестов пользовательского интерфейса теста: CodedUIExentsibilitySample  
 В этот проект входят пользовательские классы, которые используются в тестах листа Excel. Код для каждого из этих классов вполне очевиден. Тем не менее для каждого пользовательского класса представлено краткое описание. Дополнительные сведения см. в статье [Пример расширения закодированного теста пользовательского интерфейса для Excel](../test/sample-coded-ui-test-extension-for-excel.md).  
  
### <a name="deploying-your-add-in-and-extension"></a>Развертывание надстройки и расширения  
 После создания всех проектов и объектов запустите предоставленный файл `CopyDrop.bat` от имени администратора. Этот файл копирует DLL- и PDB-файлы `ExcelCodedUIAddinHelper` в следующее расположение:  
  
 "`%CommonProgramFiles(x86)%\Microsoft Shared\VSTT\<version number>\UITestExtensionPackages\*.*`", где номер версии может быть 11.0, 12.0 и т. д. в зависимости от используемой версии Visual Studio.  
  
  DLL- и PDB-файлы `ExcelUICommunicationHelper` копируются в `"%ProgramFiles(x86)%\Microsoft Visual Studio <version number>\Common7\IDE\PrivateAssemblies”`.  
  
 Возможно, понадобится изменить точные пути для копирования, но дополнительные установки не потребуются. На 64-разрядном компьютере используйте 32-разрядную командную строку Visual Studio Enterprise для запуска файла `CopyDrop.bat`.  
  
### <a name="testing-excel-with-the-sampletestproject"></a>Тестирование Excel с помощью SampleTestProject  
 Тест можно запустить в предоставленном тестовом проекте, где используется определенная версия Excel, которая может у вас отсутствовать, или можно создать собственный тестовый проект и записать свой тест. Дополнительные сведения см. в разделе [Создание закодированных тестов пользовательского интерфейса](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
## <a name="see-also"></a>См. также раздел  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)   
 [Рекомендации по выполнению закодированных тестов пользовательского интерфейса](../test/best-practices-for-coded-ui-tests.md)   
 [Поддерживаемые конфигурации и платформы для закодированных тестов пользовательского интерфейса и записей действий](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

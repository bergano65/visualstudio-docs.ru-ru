---
title: Анализ закодированных тестов пользовательского интерфейса с помощью журналов закодированных тестов пользовательского интерфейса | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 15
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7040b4dd07eebb4332634d5d8ffc1d9bc8d8c06b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686479"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Анализ закодированных тестов пользовательского интерфейса с помощью журналов закодированных тестов пользовательского интерфейса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Журналы закодированных тестов ИП фильтруют и записывают важную информацию о запуске тестов.  
  
 **Требования**  
  
- Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>Почему требуется сделать это?  
 Журналы представлены в формате, который облегчает устранение проблем.  
  
## <a name="how-do-i-do-this"></a>Инструкции  
  
### <a name="step-1-enable-logging"></a>Шаг 1. Включение ведения журнала  
 В зависимости от сценария используйте один из следующих методов, чтобы включить ведение журнала.  
  
- Целевая версия .NET Framework 4 без файла App.config присутствует в проекте теста.  
  
    - Откройте файл **QTAgent32_40.exe.config**.  
  
         По умолчанию этот файл находится в папке **\<диск:>\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Задайте требуемый уровень журнала в значении EqtTraceLevel.  
  
         Сохраните файл.  
  
- Целевая версия .NET Framework 4.5 без файла App.config присутствует в проекте теста.  
  
    - Откройте файл **QTAgent32.exe.config**.  
  
         По умолчанию этот файл находится в папке **\<диск:>\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Задайте требуемый уровень журнала в значении EqtTraceLevel.  
  
         Сохраните файл.  
  
- Файл App.config присутствует в проекте теста.  
  
    - Откройте файл App.config в проекте.  
  
         Добавьте следующий код в узле конфигурации:  
  
         `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`  
  
- Включение ведения журнала в коде теста  
  
    - <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;  
  
### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Шаг 2. Запуск кодированного теста пользовательского интерфейса и просмотр журнала  
 При запуске закодированного теста пользовательского интерфейса после внесения изменений в файл **QTAgent32.exe.config** вы увидите выходную ссылку в результатах обозревателя тестов. Если выбран подробный уровень трассировки ("verbose"), файлы журнала создаются не только при ошибке теста, но и при успешном выполнении теста.  
  
1. В меню **Тест** выберите **Окна** и щелкните **Обозреватель тестов**.  
  
2. В меню **Сборка** выберите **Собрать решение**.  
  
3. В обозревателе тестов выберите закодированный тест пользовательского интерфейса, который необходимо выполнить, откройте его контекстное меню и выберите пункт **Выполнить выбранные тесты**.  
  
     Автоматизированные тесты будут выполнены, будет предоставлена информация об их успешном выполнении или выполнении с ошибками.  
  
    > [!TIP]
    > Для просмотра обозревателя тестов из меню **Тест** наведите указатель на пункт **Окна** и выберите пункт **Обозреватель тестов**.  
  
4. В результатах обозревателя тестов щелкните ссылку **Выходные данные**.  
  
     ![Ссылка вывода в обозревателе тестов](../test/media/cuit-htmlactionlog1.png "CUIT_HTMLActionLog1")  
  
     Здесь отображаются результаты теста, содержащие ссылку на журнал действий.  
  
     ![Результаты и выходные ссылки из закодированного теста пользовательского интерфейса](../test/media/cuit-htmlactionlog2.png "CUIT_HTMLActionLog2")  
  
5. Выберите ссылку UITestActionLog.html.  
  
     Журнал появится в браузере.  
  
     ![Файл журнала закодированного теста пользовательского интерфейса](../test/media/cuit-htmlactionlog3.png "CUIT_HTMLActionLog3")  
  
## <a name="q--a"></a>Вопросы и ответы  
  
### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>Вопрос: Что произошло с разделом enablehtmllogger?  
 В предыдущих версиях Visual Studio для включения HtmlLogger в закодированном тесте ИП использовались два дополнительных параметра конфигурации:  
  
```  
  
<add key="EnableHtmlLogger" value="true"/>  
  
<add key="EnableSnapshotInfo" value="true"/>  
  
```  
  
 Начиная с Visual Studio 2012 оба параметра были удалены. EqtTraceLevel — это единственный параметр, который следует изменить, чтобы включить HtmlLogger.  
  
## <a name="see-also"></a>См. также  
 [Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)   
 [Практическое руководство. Запуск тестов из Microsoft Visual Studio](https://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)

---
title: Устранение неполадок пакетов VSPackage | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad5ab8a337d790af8cd6d800c7bf36ea6ff01286
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348687"
---
# <a name="troubleshooting-vspackages"></a>Устранение неполадок, связанных с пакетами VSPackage
Ниже приведены распространенные проблемы, которые могут возникнуть с VSPackage и советы для решения проблем.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Для устранения неполадок пакет VSPackage, который предотвращает запуск Visual Studio  
  
- Запуск [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в безопасном режиме.  
  
   Чтобы запустить [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в безопасном режиме, в командной строке введите **devenv.exe /safemode**.  
  
   Во время этого процесса загружаются нет пакетов VSPackage, за исключением пакетов VSPackage, входят в состав [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Для устранения неполадок, не загружается VSPackage  
  
1. Убедитесь, что вы используете корневой раздел реестра, в котором VSPackage регистрируется для запуска, обычно корневой раздел реестра экспериментальный.  
  
    Дополнительные сведения см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
2. Если VSPackage предназначено для запуска в корне экспериментальный реестра, убедитесь, что выполняется экспериментальной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    Для запуска экспериментальной версии, введите следующую команду: **devenv/rootsuffix exp**.  
  
3. Проверьте значения реестра VSPackage.  
  
    Дополнительные сведения см. в разделе [регистрации пакетов VSPackage](registering-and-unregistering-vspackages.md) и [пакеты VSPackage, управление](../extensibility/managing-vspackages.md).  
  
4. Откройте **вывода** окно экземпляра [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , не смог загрузить VSPackage. В этом окне могут отображаться сведения о причину сбоя загрузки VSPackage.  
  
   > [!NOTE]
   >  При запуске экспериментальной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE), проверьте **вывода** окно обеих версий.  
  
5. В журнале действий.  
  
    Дополнительные сведения см. в разделе [как: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
6. Дополнительные сведения об исключениях, создаваемых интегрированной среды разработки **исключения** на **Отладка** меню, чтобы включить исключения. В **исключения** диалоговом выберите типы исключений, о которых нужно получить дополнительные сведения.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Для устранения неполадок не регистрирует VSPackage  
  
1.  Убедитесь, что VSPackage сборка находится в надежном расположении. RegPkg не удается зарегистрировать сборок в месте ненадежному или частично доверенным, например сетевую папку в конфигурации безопасности .net по умолчанию. Несмотря на то, что каждый раз, когда пользователь создает проект в ненадежных расположениях, появится предупреждение, флажок «больше не показывать это сообщение» можно устранить это предупреждение от повторения.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Для устранения неполадок команды, не отображается или, приводит к ошибке, если щелкнуть команду  
  
1. Слияние новых или измененных команд и уже в интегрированной среде разработки, введя следующий текст в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] командной строки: **devenv/rootsuffix Exp/Setup**.  
  
2. Убедитесь, что [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно найти UI.dll для VSPackage.  
  
   1.  Найти идентификатор CLSID объекта VSPackage в пакеты разделе реестра:  
  
        HKLM\Software\Microsoft\Visual Studio\\*\<версии >* \Packages  
  
   2.  Проверьте правильность пути, задаваемый подраздел SatelliteDll.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Для устранения неполадок пакет VSPackage, который ведет себя неожиданно  
  
1.  Задайте точки останова в коде.  
  
     Хорошей отправной точкой для отладки: конструктор и метод инициализации. Также можно установить точки останова в область, которую нужно оценить, например команды меню. Чтобы включить точки останова, необходимо запустить в отладчике.  
  
    1.  В меню **Проект** выберите пункт **Свойства**.  
  
    2.  На **страницы свойств** выберите **Отладка** вкладки.  
  
    3.  В **аргументы командной строки** введите суффикс корневой среды разработки, для которых предназначено VSPackage. Например, чтобы выбрать экспериментальную сборку, введите: **RootSuffix Exp**.  
  
    4.  На **Отладка** меню, щелкните **начать отладку** или нажмите клавишу F5.  
  
        > [!NOTE]
        >  При отладке проекта, создать или загрузить существующий экземпляр проекта сейчас.  
  
2.  Использование журнала действий.  
  
     Трассировки поведение VSPackage, записывая данные в журнал действий в ключевых точках. Этот метод особенно полезен, при запуске пакета VSPackage в сфере розничной торговли. Дополнительные сведения см. в разделе [как: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Используйте открытые символы.  
  
     Для повышения удобочитаемости во время отладки, символы можно присоединить к отладчику.  
  
    1.  Из **Сервис/Параметры** меню перейдите к **отладка/символы** диалоговое окно.  
  
    2.  Добавьте этот **символов (PDB) расположение**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Для повышения производительности, укажите папку кэша символов, например:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Для устранения неполадок отсутствующих пакетов VSPackage или одну из ее зависимостей  
  
1. Для управляемого кода убедитесь в правильности пути для ссылок.  
  
   1.  В меню **Проект** выберите пункт **Свойства**.  
  
   2.  Выберите **ссылки** вкладке **страницы свойств** диалоговое окно и убедитесь, что все пути указаны правильно. Кроме того, можно использовать **обозреватель объектов** чтобы просматривать объекты, на которую указывает ссылка.  
  
        Для управляемого кода, можно использовать [Fuslogvw.exe (просмотра журнала привязки сборок)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) для получения сведений о сборке, вызвавшей сбой загрузки.  
  
2. Для неуправляемого кода, найдите идентификатор CLSID объекта VSPackage в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] системного реестра CLSID:  
  
    HKLM\Software\Microsoft\Visual Studio\\*\<версии >* \CLSID  
  
   Убедитесь, что операция InprocServer32 имеет правильный путь к библиотеке dll VSPackage.  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)
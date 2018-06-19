---
title: Устранение неполадок пакетов VSPackage | Документы Microsoft
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
ms.openlocfilehash: 73c754de72238671dd10235e792c43fb6d0a1b5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146200"
---
# <a name="troubleshooting-vspackages"></a>Устранение неполадок пакетов VSPackage
Ниже приведены распространенные проблемы, может существовать VSPackage и советы для устранения проблем.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Для устранения неполадок VSPackage, который предотвращает запуск Visual Studio  
  
-   Запустите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в безопасном режиме.  
  
     Чтобы запустить [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в безопасном режиме, в командной строке введите **/SafeMode devenv.exe**.  
  
     Во время этого процесса не пакетов VSPackage загружаются за исключением того, пакеты VSPackage, входящих в состав [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Для устранения неполадок VSPackage, не загружается  
  
1.  Убедитесь, что вы используете корневой раздел реестра, в котором VSPackage регистрируется для запуска, обычно корневой раздел экспериментальном реестра.  
  
     Дополнительные сведения см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
2.  Если пакет VSPackage предназначены для запуска в корневой раздел экспериментальном реестра, убедитесь в том, что запущены экспериментальной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Для запуска экспериментальной версии, введите в командную строку: **devenv/rootsuffix exp**.  
  
3.  Проверьте значения реестра VSPackage.  
  
     Дополнительные сведения см. в разделе [регистрации пакетов VSPackage](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) и [управления пакеты VSPackage](../extensibility/managing-vspackages.md).  
  
4.  Откройте **вывода** окна экземпляра [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , не удается загрузить пакет VSPackage. В этом окне могут отображаться сведения о том, почему VSPackage не смог загрузить.  
  
    > [!NOTE]
    >  При запуске экспериментальной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE), проверки **вывода** окна обеих версий.  
  
5.  Проверьте в журнале действий.  
  
     Дополнительные сведения см. в разделе [как: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Дополнительные сведения о исключения, создаваемые в Интегрированной среде разработки **исключения** на **отладки** меню, чтобы разрешить исключения. В **исключения** диалоговом окне выберите типы исключений, о которых вам нужна дополнительная информация.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Для устранения неполадок пакетов VSPackage, неправильно  
  
1.  Убедитесь, что сборки VSPackage находится в надежном расположении. RegPkg не удается зарегистрировать сборки в ненадежных или частичное доверие расположение, например на общем сетевом ресурсе в конфигурации по умолчанию для системы безопасности .net. Несмотря на то, что предупреждение появляется каждый раз, когда пользователь создает проект в ненадежных источников, флажок «больше не показывать это сообщение» можно устранить это предупреждение из повторения.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Для устранения неполадок команды не отображается или, приводит к ошибке при нажатии кнопки команды  
  
1.  Слияние новых или измененных команд и их интегрированной среды разработки, введя следующую команду в командной [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] командной строки: **/rootsuffix devenv/setup Exp**.  
  
2.  Убедитесь, что [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно найти UI.dll для VSPackage.  
  
    1.  Найти CLSID VSPackage в раздел реестра пакетов:  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<версии >* \Packages  
  
    2.  Проверьте правильность пути, предоставленных подраздел SatelliteDll.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Для устранения неполадок VSPackage, который ведет себя неожиданно  
  
1.  Задайте точки останова в коде.  
  
     Хорошей отправной точкой для отладки: конструктор и метод инициализации. Можно также задать точки останова в область, которую необходимо оценить, такого как команда меню. Чтобы включить точки останова, необходимо запустить в отладчике.  
  
    1.  В меню **Проект** выберите пункт **Свойства**.  
  
    2.  На **страницы свойств** выберите **отладки** вкладки.  
  
    3.  В **аргументы командной строки** введите суффикс корневой среды разработки, используемой для VSPackage. Например, чтобы выбрать экспериментальную сборку, введите: **RootSuffix Exp**.  
  
    4.  На **отладки** меню, нажмите кнопку **начать отладку** или нажмите клавишу F5.  
  
        > [!NOTE]
        >  При отладке проекта, создать или загрузить существующий экземпляр проекта теперь.  
  
2.  Использование журнала действий.  
  
     Поведение VSPackage трассировки записывая сведения в журнале активности в соответствующие моменты. Этот метод особенно полезен при выполнении пакета VSPackage в среде розничной торговли. Дополнительные сведения см. в разделе [как: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Используйте открытые символы.  
  
     Для повышения удобства чтения во время отладки, можно присоединить символы в отладчик.  
  
    1.  Из **Сервис/Параметры** меню, перейдите к **отладка/символы** диалоговое окно.  
  
    2.  Добавьте это **символов (PDB) расположение**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Для повышения производительности, укажите папку кэша символов, например:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Для устранения неполадок отсутствует VSPackage или одну из ее зависимостей  
  
1.  Для управляемого кода убедитесь в правильности пути для ссылок.  
  
    1.  В меню **Проект** выберите пункт **Свойства**.  
  
    2.  Выберите **ссылки** вкладке **страницы свойств** диалоговое окно и убедитесь, что все пути указаны правильно. Кроме того, можно использовать **обозревателя объектов** поиск объектов, на которую указывает ссылка.  
  
         Для управляемого кода, можно использовать [Fuslogvw.exe (просмотра журнала привязки сборок)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) для отображения сведений о сборке, вызвавшей сбой загрузки.  
  
2.  Для неуправляемого кода найти CLSID VSPackage в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] узла в реестре CLSID:  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<версии >* \CLSID  
  
 Убедитесь в том, что запись InprocServer32 имеет правильный путь к dll пакета VSPackage.  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)
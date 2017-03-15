---
title: "Устранение неполадок пакетов VSPackages | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 933b0177e3287717b2cfb900996b947db7034ee5
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-vspackages"></a>Устранение неполадок пакеты VSPackage
Ниже приведены распространенные проблемы, которые могут возникнуть с VSPackage и советы по устранению.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Для устранения неполадок VSPackage, который предотвращает запуск Visual Studio  
  
-   Запустите [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в безопасном режиме.  
  
     Чтобы запустить [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] в безопасном режиме, в командной строке введите **devenv.exe /safemode**.  
  
     Во время этого процесса не VSPackages загружаются только пакеты VSPackage, включенных в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Для устранения неполадок VSPackage, который не загружена  
  
1.  Убедитесь, что вы используете корневой раздел реестра, в котором VSPackage регистрируется для запуска, обычно корневой раздел реестра экспериментальном.  
  
     Дополнительные сведения см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
2.  Если VSPackage предназначена для запуска в корне экспериментальном реестра, убедитесь, что запущены экспериментальной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Для запуска экспериментальной версии, введите следующую команду: **devenv/rootsuffix exp**.  
  
3.  Проверьте элементы реестра VSPackage.  
  
     Дополнительные сведения см. в разделе [регистрация VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) и [управление VSPackages](../extensibility/managing-vspackages.md).  
  
4.  Откройте **вывода** окно экземпляра [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , не удается загрузить VSPackage. В этом окне могут отображаться сведения о почему VSPackage не удается загрузить.  
  
    > [!NOTE]
    >  При запуске экспериментальной версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE), проверьте **вывода** окно обеих версий.  
  
5.  Проверьте журнал активности.  
  
     Дополнительные сведения см. в разделе [Практическое руководство: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Дополнительные сведения о исключения в интегрированной среде разработки **исключения** на **отладки** меню, чтобы включить исключения. В **исключения** диалоговом окне выберите типы исключений, о которых вам нужна дополнительная информация.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Для устранения неполадок VSPackage, который не зарегистрирован  
  
1.  Убедитесь, что сборка VSPackage находится в надежном расположении. RegPkg не удается зарегистрировать сборки в ненадежному или частично доверенным расположение, например сетевую папку в конфигурации по умолчанию для безопасности .net. Несмотря на то, что всякий раз, когда пользователь создает проект в ненадежных источников, выводится предупреждение, флажок «не показывать это сообщение» можно устранить это предупреждение от повторения.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Для устранения неполадок команды не отображается, или, выдает ошибку при выборе команды  
  
1.  Слияние новых или измененных команд и уже в Интегрированной среде разработки, введя следующее в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] командной строки: **devenv/rootsuffix Exp/Setup**.  
  
2.  Убедитесь, что [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно найти UI.dll VSPackage.  
  
    1.  Найти CLSID VSPackage пакеты из раздела реестра:  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<версии настроек*\Packages  
  
    2.  Проверьте правильность пути, предоставленному подраздел SatelliteDll.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Для устранения неполадок VSPackage, который ведет себя неожиданно  
  
1.  Задайте точки останова в коде.  
  
     Конструктор и метод инициализации, являются хорошей отправной точкой для отладки. Можно также задать точки останова в область, которую необходимо оценить, например, команда меню. Для включения точек останова, необходимо запустить в отладчике.  
  
    1.  На **проекта** меню, щелкните **свойства**.  
  
    2.  На **страницы свойств** диалоговом **отладки** вкладки.  
  
    3.  В **аргументы командной строки** введите суффикс корневой среды разработки, ваши цели VSPackage. Например, чтобы выбрать экспериментальном построении, введите: **RootSuffix Exp**.  
  
    4.  На **отладки** меню, щелкните **начать отладку** или нажмите клавишу F5.  
  
        > [!NOTE]
        >  При отладке проекта, создать или загрузить существующий экземпляр проекта теперь.  
  
2.  Используйте журнал действий.  
  
     Записывая данные в журнале активности в ключевых точках трассировки поведение VSPackage. Этот метод особенно полезен при выполнении в среде розничной торговли VSPackage. Дополнительные сведения см. в разделе [Практическое руководство: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Используйте открытые символы.  
  
     Для повышения удобочитаемости во время отладки можно присоединить символов в отладчике.  
  
    1.  От **Сервис/Параметры** меню, перейдите к **отладка и символы** диалоговое окно.  
  
    2.  Добавьте это **символов (PDB) расположение**:  
  
         [http://MSDL.Microsoft.com/download/Symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Для повышения производительности, укажите папку кэша символов, например:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Для устранения недостающих VSPackage или одна из его зависимостей  
  
1.  Для управляемого кода убедитесь, что правильность пути для ссылок.  
  
    1.  На **проекта** меню, щелкните **свойства**.  
  
    2.  Выберите **ссылки** вкладке **страницы свойств** диалоговое окно и убедитесь, что все пути указаны правильно. Кроме того, можно использовать **обозревателя объектов** поиск объектов, на которые имеются ссылки.  
  
         Для управляемого кода, можно использовать [Fuslogvw.exe (просмотра журнала привязки сборок)](http://msdn.microsoft.com/Library/e32fa443-0778-4cc3-bf36-5c8ea297d296) для отображения сведений о загрузке сборки.  
  
2.  Для неуправляемого кода, найти CLSID VSPackage в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] узла в реестре CLSID:  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<версии настроек*\CLSID  
  
 Убедитесь в том, что операция InprocServer32 имеет правильный путь к VSPackage dll.  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)

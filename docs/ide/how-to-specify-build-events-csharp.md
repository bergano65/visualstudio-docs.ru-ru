---
title: "Практическое руководство. Назначение событий построения (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "события построения [Visual Studio]"
  - "построения [Visual Studio], события"
  - "события [Visual Studio], сборки"
  - "события после построения"
  - "событие перед построением"
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Практическое руководство. Назначение событий построения (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

События построения позволяют указать команды, которые выполняются до начала построения или после ее завершения.  События построения выполняются, только если в процессе построения успешно выполняются эти этапы.  
  
 При построении проекта, события перед построением добавляются в файл с именем PreBuildEvent.bat, а события после построения добавляются в файл с именем PostBuildEvent.bat.  Если требуется обеспечить проверку ошибок, добавьте собственные команды проверки ошибок к этапам построения.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Как указать события перед и после построения  
  
#### Чтобы указать событие построения  
  
1.  В **Обозревателе решений** выберите проект, для которого требуется указать событие построения.  
  
2.  В меню **Проект** выберите пункт **Свойства**.  
  
3.  Перейдите на вкладку **События построения**.  
  
4.  В поле **Командная строка событий до построения** укажите синтаксис события построения.  
  
    > [!NOTE]
    >  События перед построением не запускаются, если проект был обновлен, и построение не запускалось.  
  
5.  В поле **Командная строка события после построения** укажите синтаксис события построения.  
  
    > [!NOTE]
    >  Добавьте оператор `call` перед всеми командами после построения, запускающими файлы с расширением BAT.  Например, `call C:\MyFile.bat` или `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
6.  В поле **Выполнить событие после построения** укажите при каких условиях событие должно запускаться.  
  
    > [!NOTE]
    >  Для добавления длинного синтаксиса или для выбора макроса построения из [Диалоговое окно "Командная строка события "После построения"" или "Командная строка события "До построения""](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), нажмите кнопку с многоточием \(**…**\) для отображения окна редактирования.  
  
     Синтаксис события построения может включать любую команду, допустимую в командной строке или в BAT\-файле.  Перед именем пакетного файла необходимо указывать `call` для обеспечения выполнения всех последующих команд.  
  
     **Примечание** Если созданные события перед построением или события после построения не выполняются успешно, можно прервать построение: нужно выполнить выход действия события с кодом, отличающимся от нуля \(0\), что означает успешное действие.  
  
## Пример: как изменить данные манифеста с помощью событий после построения  
 В следующей процедуре показана установка минимальной версии операционной системы в манифесте приложения с помощью команды .exe, вызываемой из события после построения \(файл .exe.manifest в каталоге проекта\).  Минимальная версия операционной системы — это число из четырех частей, например 4.10.0.0.  Для этого команда изменит раздел `<dependentOS>` манифеста.  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### Чтобы создать команду .exe для изменения манифеста приложения  
  
1.  Создайте консольное приложение для команды.  В меню **Файл** выберите **Создать** и щелкните **Проект**.  
  
2.  В диалоговом окне **Новый проект** разверните **Visual C\#**, щелкните **Windows** и затем выберите шаблон **Консольное приложение**.  Назовите проект `ChangeOSVersionCS`.  
  
3.  В Program.cs добавьте следующую строку к другим инструкциям `using` в верхней части файла:  
  
    ```  
    using System.Xml;  
    ```  
  
4.  В пространстве имен `ChangeOSVersionCS` замените реализацию класса `Program` следующим кодом:  
  
    ```  
    class Program  
    {  
       /// <summary>  
       /// This function will set the minimum operating system version for a ClickOnce application.  
       /// </summary>  
       /// <param name="args">  
       /// Command Line Arguments:  
       /// 0 - Path to application manifest (.exe.manifest).  
       /// 1 - Version of OS  
       ///</param>  
       static void Main(string[] args)  
       {  
          string applicationManifestPath = args[0];  
          Console.WriteLine("Application Manifest Path: " + applicationManifestPath);  
  
          // Get version name.  
          Version osVersion = null;  
          if (args.Length >=2 ){  
             osVersion = new Version(args[1]);  
          }else{  
             throw new ArgumentException("OS Version not specified.");  
          }  
          Console.WriteLine("Desired OS Version: " + osVersion.ToString());  
  
          XmlDocument document;  
          XmlNamespaceManager namespaceManager;  
          namespaceManager = new XmlNamespaceManager(new NameTable());  
          namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");  
          namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");  
  
          document = new XmlDocument();  
          document.Load(applicationManifestPath);  
  
          string baseXPath;  
          baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";  
  
          // Change minimum required operating system version.  
          XmlNode node;  
          node = document.SelectSingleNode(baseXPath, namespaceManager);  
          node.Attributes["majorVersion"].Value = osVersion.Major.ToString();  
          node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();  
          node.Attributes["buildNumber"].Value = osVersion.Build.ToString();  
          node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();  
  
          document.Save(applicationManifestPath);  
       }  
    }  
    ```  
  
     Команда принимает два аргумента: путь к манифесту приложения \(то есть папка в которой процесс построения создает манифест, обычно Projectname.Publish\) и новая версия операционной системы.  
  
5.  Выполните построение проекта.  В меню **Построение** выберите **Построить решение**.  
  
6.  Скопируйте файл EXE в каталог, например `C:\TEMP\ChangeOSVersionVB.exe`.  
  
 Далее, внесите эту команду в событие после построения для изменения манифеста приложения.  
  
#### Чтобы внести событие после построения для изменения манифеста приложения  
  
1.  Создайте приложение Windows для проекта, который должен быть опубликован.  В меню **Файл** выберите **Создать** и щелкните **Проект**.  
  
2.  В диалоговом окне **Новый проект** разверните **Visual C\#**, щелкните **Windows** и затем выберите шаблон **Приложение Windows Forms**.  Назовите проект `CSWinApp`.  
  
3.  Выберите проект в **Обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
4.  В конструкторе проектов перейдите на страницу **Публикация** и задайте **Расположение публикации** на  `C:\TEMP\` .  
  
5.  Опубликуйте проект, щелкнув **Опубликовать сейчас**.  
  
     Файл манифеста будет построен и помещен в  `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest` .  Для просмотра манифеста, щелкните правой кнопкой мыши файл и выберите **Открыть с помощью**, а затем щелкните **Выбрать программу из списка** и выберите **Блокнот**.  
  
     Найдите в файле элемент `<osVersionInfo>`.  Например, версия может быть:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  В конструкторе проектов перейдите на вкладку **События построения** и нажмите кнопку **Изменить событие после построения**.  
  
7.  В поле **Командная строка событий после построения** введите следующую команду:  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     При построении проекта эта команда приведет к изменению в манифесте приложения минимальной версии операционной системы на 5.1.2600.0.  
  
     Поскольку макрос `$(TargetPath)` выражает полный путь к создаваемому исполняемому файлу, `$(TargetPath)`.manifest будет указывать манифест приложения, созданный в папке Bin.  Публикация скопирует этот манифест в расположение публикаций, которое было установлено ранее.  
  
8.  Опубликуйте проект еще раз.  Перейдите на страницу **Публикации** и выберите **Опубликовать сейчас**.  
  
     Просмотрите манифест еще раз.  Чтобы просмотреть манифест, перейдите в каталог публикаций, щелкните правой кнопкой мыши файл и укажите **Открыть с помощью** и щелкните **Выбрать программу из списка**, а затем **Блокнот**.  
  
     Теперь версия должна быть:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## См. также  
 [Страница "Событий построения" в конструкторе проектов \(C\#\)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [Диалоговое окно "Командная строка события "После построения"" или "Командная строка события "До построения""](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Практическое руководство. Указание событий построения \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Построение приложений в Visual Studio](../ide/compiling-and-building-in-visual-studio.md)
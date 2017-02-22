---
title: "Практическое руководство: Создание пользовательского текста маркеры | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - маркеры пользовательский текст"
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: Создание пользовательского текста маркеры
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Если вы хотите создать пользовательский текст маркера для выделения или организации кода, необходимо выполнить следующие действия:  
  
-   Регистрация текстового маркера доступа к нему другими средствами  
  
-   Реализация по умолчанию и конфигурации текстовой метки  
  
-   Создать службу, которая может использоваться другими процессами, чтобы сделать использование текстовой метки  
  
 Подробные сведения по применению текстовая метка область кода, в разделе [как: использование текстовых меток](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Чтобы зарегистрировать пользовательский маркер  
  
1.  Создайте запись реестра следующим образом:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< версии>*маркеры \Text Editor\External\\*\< MarkerGUID>*  
  
     *\< MarkerGUID>*— `GUID` используется для идентификации добавляемого маркера  
  
     *\< версия>* версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], например 8.0  
  
     *\< PackageGUID>* — это GUID VSPackage, реализующий объект автоматизации.  
  
    > [!NOTE]
    >  Путь к корневому каталогу HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< версии>* может быть переопределен с альтернативным корнем при инициализации оболочки Visual Studio, Дополнительные сведения см. в разделах, [переключателей командной строки](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2.  Создание четырех значений в разделе HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\< версии>*\Text Editor\External маркеры\\*\< MarkerGUID>*  
  
    -   (Значение по умолчанию)  
  
    -   Служба  
  
    -   DisplayName  
  
    -   Пакет  
  
    -   `Default` является необязательным элементом типа REG_SZ. Если задано значение параметра является строкой, содержащей некоторые полезные идентификационные сведения, например «пользовательский текст маркером».  
  
    -   `Service` — запись типа REG_SZ, содержащий строку идентификатора GUID службы, которая предоставляет пользовательский текст маркера, proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Формат: {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
    -   `DisplayName` запись типа REG_SZ, содержащий идентификатор ресурса имени настраиваемого текстового маркера. Формат — #YYYY.  
  
    -   `Package` запись типа REG_SZ, содержащего `GUID` VSPackage, который предоставляет службы отображается в узле службы. Формат: {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Для создания маркера пользовательский текст  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> интерфейса.  
  
     Реализации этого интерфейса определяет поведение и внешний вид типа пользовательских маркеров.  
  
     Этот интерфейс называется  
  
    1.  Пользователь запускает интегрированной среды Разработки в первый раз.  
  
    2.  Пользователь выбирает **Восстановить значения по умолчанию** под заголовком **шрифты и цвета** на странице свойств в **среде** Папка на левой панели **Параметры** получен диалогового **средства** меню интегрированной среды разработки.  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> метод, указывая, что `IVsPackageDefinedTextMarkerType` реализации должны быть возвращаются в зависимости от типа маркера GUID, указанного в вызове метода.  
  
     Среда вызывает этот метод первый времени создается тип пользовательского маркера и указывает идентификатор GUID, определяющий тип пользовательского маркера.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Для предложения типа маркера как службы  
  
1.  Вызов <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> возвращается.  
  
2.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> метод, указав идентификатор GUID, определение пользовательских маркеров типа службы и предоставляя указатель на вашу реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейса. Ваш <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> реализации должен вернуть указатель на вашу реализацию <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> интерфейса.  
  
     Уникальный файл cookie, указывающий, что возвращается к службе. Позже можно использовать этот файл cookie отменять пользовательский маркер типа службы путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> интерфейса, задав это значение файла cookie.  
  
## <a name="see-also"></a>См. также  
 [С помощью текстовых маркеров с API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Практическое руководство: Добавление маркеров стандартный текст](../extensibility/how-to-add-standard-text-markers.md)   
 [Практическое руководство: реализации маркеры ошибки](../extensibility/how-to-implement-error-markers.md)   
 [Практическое руководство: использование текстовых меток](../extensibility/how-to-use-text-markers.md)
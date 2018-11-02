---
title: 'Практическое: Создание настраиваемых текстовых маркеров | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88828eb5abbb9a4e81d69bae9662c291cf5fd9b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885711"
---
# <a name="how-to-create-custom-text-markers"></a>Практическое: Создание настраиваемых текстовых маркеров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вы хотите создать пользовательский текстовый маркер выделить или организации кода, выполните следующие действия:  
  
- Регистрация нового текстового маркера, доступа к ней другие средства  
  
- Реализация по умолчанию и конфигурация текстового маркера  
  
- Создание службы, который может использоваться другими процессами, чтобы сделать использование текстового маркера  
  
  Сведения о способах применения текстового маркера в область кода, см. в разделе [как: используйте текстовые метки](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Чтобы зарегистрировать пользовательский маркер  
  
1. Создайте запись реестра следующим образом:  
  
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<версии >* маркеры \Text Editor\External\\*\<MarkerGUID >*  
  
    <em>\<MarkerGUID ></em>является `GUID` используется для идентификации добавляемого маркера  
  
    *\<Версии >* — это версия [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], например 8.0  
  
    *\<PackageGUID >* – идентификатор GUID VSPackage, реализующий объект автоматизации.  
  
   > [!NOTE]
   >  Путь к корневому каталогу HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<версии >* может быть переопределен альтернативным корневым, если инициализируется оболочки Visual Studio, Дополнительные сведения см. [Параметры командной строки](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Создайте четыре значения в разделе HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<версии >* \Text Editor\External маркеры\\*\<MarkerGUID >*  
  
   -   (Значение по умолчанию)  
  
   -   Служба  
  
   -   DisplayName  
  
   -   Пакет  
  
   -   `Default` является необязательным элементом типа REG_SZ. Если задано, значение параметра является строка, содержащая некоторые полезные идентификационные данные, например «Custom текстового маркера».  
  
   -   `Service` — запись типа REG_SZ, содержащий строку идентификатора GUID службы, которая предоставляет настраиваемые текстового маркера, proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Формат — {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   -   `DisplayName` запись типа REG_SZ, содержащая идентификатор ресурса имени пользовательского текстового маркера. Формат — #YYYY.  
  
   -   `Package` запись типа REG_SZ, содержащего `GUID` VSPackage, предоставляющий службы отображается в узле службы. Формат — {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Для создания маркера пользовательского текста  
  
1.  Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     Реализации этого интерфейса определяет поведение и внешний вид вашего пользовательского типа маркера.  
  
     Этот интерфейс вызывается, когда  
  
    1.  Пользователь запускает интегрированной среды разработки в первый раз.  
  
    2.  Пользователь выбирает **сбросить значение по умолчанию —** под кнопкой **шрифты и цвета** страницы свойств в **среды** папка на левой панели  **Параметры** получен диалоговое окно **средства** меню интегрированной среды разработки.  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> метод, указывая, что `IVsPackageDefinedTextMarkerType` реализации должны быть возвращаются в зависимости от типа маркера идентификатор GUID, указанный в вызове метода.  
  
     Среда вызывает этот метод первый раз создается вашего пользовательского типа маркера, а также указывает идентификатор GUID, указывающий тип пользовательского маркера.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Предложить ваш тип маркера как услуга  
  
1.  Вызовите <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> возвращается.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> метод, указывая идентификатор GUID службы тип пользовательского маркера идентификации и передачи указателя на вашу реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейс. Ваш <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> реализация должна возвращать указатель на вашу реализацию <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> интерфейс.  
  
     Уникальный файл cookie, определяющий, что службы возвращается. Позже можно использовать этот файл cookie отозвать службу пользовательские маркеры типа путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> метод <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> интерфейса, задав это значение файла cookie.  
  
## <a name="see-also"></a>См. также  
 [С помощью меток текста с помощью API прежних версий](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Практическое: Добавление стандартные текстовые метки](../extensibility/how-to-add-standard-text-markers.md)   
 [Практическое: реализовать маркеры ошибок](../extensibility/how-to-implement-error-markers.md)   
 [Практическое руководство. Использование текстовых маркеров](../extensibility/how-to-use-text-markers.md)


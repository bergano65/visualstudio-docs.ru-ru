---
title: 'Практическое: извлечение сведений строки запроса в Интернет-приложении ClickOnce | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 808e6a8d6264f616eec7716ddeb173bfccb906bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573437"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Практическое руководство. Извлечение сведений строки запроса в интернет-приложении ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: получить данные строки запроса в интерактивном приложении ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application).  
  
*Строка запроса* — это часть URL-адреса, начинающаяся с вопросительного знака (?) и содержащая произвольные сведения в форме *имя=значение*. Предположим, что имеется приложение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] с именем `WindowsApp1`, размещенное в `servername`, и вы хотите передать значение для переменной `username` при запуске приложения. URL-адрес может выглядеть следующим образом:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Две следующие процедуры показывают, как использовать приложение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] для получения сведений о строке запроса.  
  
> [!NOTE]
>  Передать сведения в строке запроса можно только при запуске приложения с использованием протокола HTTP вместо общей папки или локальной файловой системы.  
  
 В первой процедуре показано, как приложение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] может использовать небольшой фрагмент кода для считывания этих значений при запуске.  
  
 Далее показано, как настроить приложение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] с помощью MageUI.exe, чтобы оно могло принимать параметры строки запроса. Это потребуется сделать при публикации приложения.  
  
> [!NOTE]
>  Прежде чем принять решение о включении этой функции, ознакомьтесь с подразделом "Безопасность" ниже.  
  
 Сведения о создании [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания с помощью Mage.exe или MageUI.exe см. в разделе [Пошаговое руководство: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
>  Начиная с .NET Framework 3.5 с пакетом обновления 1 (SP1), аргументы командной строки можно передать автономному приложению [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Если требуется передать аргументы в приложение, можно передать параметры в файл ярлыка с помощью расширения .APPREF-MS.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Получение сведений о строке запроса из приложения ClickOnce  
  
1.  Включите в проект приведенный ниже код. Чтобы этот код работал, потребуется иметь ссылку на System.Web и добавить операторы `using` или `Imports` для System.Web, System.Collections.Specialized и System.Deployment.Application.  
  
     [!code-csharp[ClickOnceQueryString#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceQueryString/CS/Form1.cs#1)]
     [!code-vb[ClickOnceQueryString#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceQueryString/VB/Form1.vb#1)]  
  
2.  Вызовите определенную ранее функцию, чтобы получить <xref:System.Collections.DictionaryBase.Dictionary%2A> параметров строки запроса, индексированных по имени.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Включение передачи строки запроса в приложении ClickOnce с помощью MageUI.exe  
  
1.  Откройте окно командной строки платформы .NET и введите:  
  
    ```  
    MageUI  
    ```  
  
2.  Из **файл** меню, выберите **откройте**и откройте манифест развертывания для вашей [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение, которое является файлом заканчиваются на `.application` расширения.  
  
3.  Выберите панель **Параметры развертывания** в левом окне переходов и установите флажок **Разрешать передачу параметров URL-адресов в приложение** .  
  
4.  В меню **Файл** выберите команду **Сохранить**.  
  
> [!NOTE]
>  Кроме того, можно включить передачу строки запроса в [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Установите флажок **Разрешать передачу параметров URL-адресов в приложение** , который можно найти, открыв **Свойства проекта**, выбрав вкладку **Публикация** , нажав кнопку **Параметры** , а затем выбрав **Манифесты**.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 При использовании параметров строки запроса необходимо тщательно обдумать процедуру установки и активации приложения. Если приложение настроено для установки на компьютере пользователя из Интернета или из общей сетевой папки, весьма вероятно, что пользователь активирует приложение всего один раз с помощью URL-адреса. После этого пользователь будет активировать приложение уже с помощью ярлыка в меню **Пуск** . В результате приложение гарантированно получит аргументы строки запроса только один раз за все время своего существования. Если вы решили сохранить эти аргументы на компьютере пользователя для последующего использования, именно вы несете ответственность за их безопасное хранение.  
  
 Если приложение работает только в сети, оно всегда будет активироваться через URL-адрес. Но даже в этом случае приложение должно обеспечивать правильную работу в ситуациях, когда параметры строки запроса отсутствуют или повреждены.  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Разрешайте передачу параметров URL-адреса в свое приложение [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] только в том случае, если вы планируете очищать входные данные от любых вредоносных символов перед использованием. При отсутствии фильтрации SQL-запросов к базе данных строка с внедренными кавычками, символами косой черты или точками с запятой может, например, выполнять произвольные операции с данными. Дополнительные сведения о безопасности строки запроса см. в разделе [Script Exploits Overview](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
## <a name="see-also"></a>См. также  
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)




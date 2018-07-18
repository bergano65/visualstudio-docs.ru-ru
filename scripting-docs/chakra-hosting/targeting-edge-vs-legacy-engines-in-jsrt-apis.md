---
title: Работа с модулем Edge и модулями предыдущих версий в API JsRT | Документы Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cbc7df6c-0bc9-48f5-b9ad-b9ed31c42f92
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50947cbd619f086daecc1e09f88a4b238a36ee41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569604"
---
# <a name="targeting-edge-vs-legacy-engines-in-jsrt-apis"></a>Работа с модулем Edge и модулями предыдущих версий в API JsRT.
Начиная с Windows 10, одним из изменений, внесенных в Chakra (обработчик JavaScript), которое соответствует стратегии браузера Windows 10 по поддержке нового механизма визуализации Edge, является поддержка двух разных моделей Chakra:  
  
-   Старый модуль Chakra (также называемый *модулем предыдущих версий* или jscript9.dll ниже), который поставляется вместе с Internet Explorer 11 и поддерживает данный обозреватель. Этот модуль сейчас заморожен и не будет фундаментально изменяться по сравнению с версией Win8.1/IE11.  
  
-   Новый модуль Chakra (также называемый *модулем Edge* или chakra.dll ниже) поставляется вместе с новым браузером в Windows 10 (Microsoft Edge) и поддерживает его. Этот модуль будет постоянно обновляться и поддерживать динамический модуль [Edge](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx). Понятие «активный» подразумевает, что, в отличие от модуля предыдущих версий, такой модуль не будет переносить функцию скрипта управления версиями ни в какой форме.  
  
 При создании приложения с помощью API размещения среды выполнения JavaScript (JsRT) можно ориентироваться либо на модуль предыдущих версий, либо на модуль Edge.  
  
-   Если необходимо обеспечивать обратную совместимость существующих приложений, следует выбрать модуль предыдущих версий.  
  
-   Если же необходимо, чтобы приложение было нацелено на новые функции JavaScript по мере их выпуска (например, ECMAScript 6) и поддерживало их, следует использовать модуль Edge.  
  
 В этом разделе описываются способы нацеливания на модули различного типа.  
  
## <a name="target-your-preferred-version"></a>Нацеливание на предпочтительную версию  
 При создании приложения можно выбрать версию JsRT, которая поддерживает либо модуль Edge, либо модуль предыдущих версий. При выборе версии JsRT используйте рекомендации, приведенные выше. Чтобы подчеркнуть указанные различия, в `JsCreateRuntime`, `JsCreateContext`и `JsStartDebugging`были внесены следующие изменения.  
  
 Для `JsCreateRuntime`:  
  
-   При нацеливании на модуль предыдущих версий значение перечисления `JsRuntimeVersionEdge` не рекомендуется и в сообщении будет предложено вместо него применять значение `JsRuntimeVersionInternetExplorer11` .  
  
-   При нацеливании на модуль Edge параметр версии исключается из функции `JsCreateRuntime` .  
  
    ```cpp  
    JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
    ```  
  
 Для `JsCreateContext` и `JsStartDebugging`:  
  
-   При нацеливании на модуль предыдущих версий интерфейс `IDebugApplication` предоставляет ваши собственные методы неудаленной отладки. Для отладки функции `JsCreateContext` и `JsStartDebugging` в качестве параметра используйте `IDebugApplication` .  
  
-   При нацеливании на модуль Edge интерфейс `IDebugApplication` применять не рекомендуется. Модуль Chakra реализует возможности отладки машинного кода и скрипта с помощью отладчика Visual Studio и не требует, чтобы пользователь реализовал `IDebugApplication` . В результате, интерфейс больше не является параметром для `JsCreateContext` и `JsStartDebugging` .  
  
 Сигнатуры для старых API-интерфейсов в модуле предыдущих версий выглядят следующим образом:  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsRuntimeVersion version, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, IDebugApplication *debugApplication, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging(IDebugApplication *debugApplication);  
```  
  
 Сигнатуры для старых API-интерфейсов в модуле Edge выглядят следующим образом:  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging();  
```  
  
## <a name="compile-for-your-preferred-version-using-visual-c"></a>Компиляция предпочтительной версии с помощью Visual C++  
 При использовании Visual C++ импортируйте JsRT API, включив заголовок jsrt.h, и убедитесь, что файл jsrt.lib включен в список входных файлов вашего компоновщика:  
  
```cpp  
#include <jsrt.h>  
```  
  
 ![Добавление jsrt.lib в качестве входного файла компоновщика](../chakra-hosting/media/js-chakra.png "JS_Chakra_")  
  
 Если необходимо использовать двоичные файлы модуля Edge, нужно определить макрос `USE_EDGEMODE_JSRT` перед включением jsrt.h и связать не с jsrt.lib, а с chakrart.lib:  
  
```cpp  
#define USE_EDGEMODE_JSRT  
#include <jsrt.h>  
```  
  
 ![Добавление chakrart.lib в качестве входного файла компоновщика](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting_")  
  
 Если вы начинаете с нового приложения, то можно начать создавать код в соответствии с JsRT API.  
  
## <a name="compile-for-your-preferred-version-using-net"></a>Компиляция предпочтительной версии с помощью .NET  
 Если вы используете .NET и P/Invoke, необходимо изменить объявления JsRT API [DllImport] для импорта chakra.dll вместо jscript9.dll. Кроме того, измените определение для `JsCreateRuntime` , чтобы удалить параметр `JsRuntimeVersion` , и определение для `JsCreateContext` и `JsStartDebugging` , чтобы удалить параметр `IDebugApplication` .  
  
 Для модуля предыдущих версий используйте следующий код.  
  
```c#  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsRuntimeVersion version,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    IDebugApplication debugApplication,  
    out JsContextRef newContext  
);   
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsStartDebugging(  
    IDebugApplication debugApplication,  
);  
```  
  
 Для модуля Edge используйте следующий код.  
  
```c#  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    out JsContextRef newContext  
);   
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsStartDebugging();  
```  
  
> [!CAUTION]
>  Если вы вручную маршалируете указатель функции (например, через LoadLibrary/GetProcAddress), очень важно не смешивать объявления метода. Иначе стек будет несбалансирован, что приведет к непредсказуемому поведению, например к сбою приложения. Та же проблема будет возникать, если вы выполняете глобальный поиск и замену экземпляров файла jscript9.dll в коде импорта, так как вам будет не хватать удаленного параметра `version`.  
  
## <a name="summary"></a>Сводка  
 В Windows 10 API-интерфейсы размещения среды выполнения JavaScript подразделяются на две группы. Теперь эти API-интерфейсы поддерживают "активный" модуль Edge, для которого возможности языка будут соответствовать "активному" модулю Edge в Microsoft Edge. Эти возможности можно использовать из классических приложений или приложений магазина для создания новых интересных способов расширения приложения, а также применения современных веб-навыков в существующей базе кода. Но так как между предыдущими версиями есть небольшие различия, при выборе модуля Edge или модуля предыдущих версий необходимо учитывать следующие моменты.  
  
-   Ваше приложение может поддерживать только одну версию JsRT для каждого процесса.  
  
     Например, нельзя создать среду выполнения для модуля Edge, а затем среду выполнения для модуля предыдущих версий и надеяться, что они будут корректно работать в одном и том же процессе. Такая возможность не поддерживается, и это может привести к непредсказуемому поведению, например к сбою загрузки второй библиотеки DLL.  
  
-   Если использовать модуль Edge, ваше приложение может неожиданно получить новые функции при автоматическом обновлении базовой платформы.  
  
     Например, в Internet Explorer 11 режим функционирования старой среды выполнения поддерживает объявления переменных, связанных с областью действия блока, таких как `let` и `const`. Если поведение при автоматическом управлении версиями модуля Edge раньше было стандартным, код, работавший в режиме Internet Explorer 10, который не имел правил, связанных с областью действия блока, может начать функционировать с ошибками при автоматическом обновлении платформы. Это необходимо учитывать при выборе модели среды выполнения. Хотя мы всегда рекомендуем применять модуль Edge, необходимо крайне осторожно использовать структуры кода JavaScript, которые могут оказаться недопустимыми в будущем.  
  
-   JsRT для магазина Windows поддерживает только модуль Edge (chakra.dll). Приложения, пытающиеся связаться с любым API-интерфейсом JsRT в файле jscript9.dll, сертификацию не пройдут.  
  
-   Крайне важно не смешивать объявления для `JsCreateRuntime`, `JsCreateContext`и `JsStartDebugging` между jscript9.dll и chakra.dll, так как это приведет к несбалансированости стека.  
  
     При использовании C и C++ будет появляться сообщение об ошибке компоновщика при попытке использования неверного объявления до тех пор, пока вы не выполните какое-либо действие, например вызов `LoadLibrary`, а затем `GetProcAddress`. Разработчики .NET не всегда смогут легко обнаружить эту проблему, поэтому при использовании данной функции следует внимательно проверять код.  
  
## <a name="see-also"></a>См. также  
 [Размещение среды выполнения JavaScript](../chakra-hosting/javascript-runtime-hosting.md)
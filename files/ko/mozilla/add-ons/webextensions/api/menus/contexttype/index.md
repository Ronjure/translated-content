---
title: menus.ContextType
slug: Mozilla/Add-ons/WebExtensions/API/menus/ContextType
translation_of: Mozilla/Add-ons/WebExtensions/API/menus/ContextType
original_slug: Mozilla/Add-ons/WebExtensions/API/contextMenus/ContextType
---
{{AddonSidebar()}}

메뉴 항목이 나타나게 하는 콘텍스트들.

## 자료형

이 자료형의 값은 문자열이다. 항목은 주어진 콘텍스트일 때 표시된다. 가능한 값은:

- all
  - : 'all'은 'bookmark', 'tab' 그리고 'tools_menu'를 뺀 나머지 모든 콘텍스트를 다 나열한 것과 같다.
- audio
  - : [audio](/ko/docs/Web/HTML/Element/audio) 요소를 콘텍스트-클릭할 때 적용된다. (역주: 콘텍스트-클릭은 보통 마우스 오른쪽 버튼을 클릭하는 것이다)
- bookmark
  - : 툴바나 메뉴에서 북마크 항목을 콘텍스트-클릭할 때 적용된다. 현재 북마크 사이드바나 라이브러리 윈도우 항목에서는 동작하지 않는다. manifest에 "bookmarks" [API 권한](/en-US/Add-ons/WebExtensions/manifest.json/permissions#API_permissions)이 있어야 한다.
- browser_action
  - : 브라우저 액션에서 콘텍스트-클릭을 할 때 적용된다. 최대로 추가할 수 있는 최상위 브라우저 액션 콘텍스트 매뉴 항목의 수는 {{WebExtAPIRef("menus.ACTION_MENU_TOP_LEVEL_LIMIT")}}지만 서버메뉴에는 얼마든지 추가할 수 있다.
- editable
  - : 편집 가능한 요소, 가령은 [textarea](/ko/docs/Web/HTML/Element/textarea)를 콘텍스트-클릭할 때 적용된다.
- frame
  - : 내포된 [iframe](/ko/docs/Web/HTML/Element/iframe)을 콘텍스트-클릭할 때 적용된다.
- image
  - : 이미지를 콘텍스트-클릭할 때 적용된다.
- link
  - : 링크를 콘텍스트-클릭할 때 적용된다.
- page
  - : 페이지를 콘텍스트-클릭할 때 적용된다. 단, 페이지의 다른 콘텍스트가 적용되지 않을 때만이다(예를 들면, 클릭이 이미지나 내포된 iframe 또는 링크가 아니여야 한다).
- page_action
  - : 페이지 액션을 콘텍스트-클릭할 때 적용된다. 최대로 추가할 수 있는 최상위 페이지 액션 콘텍스트 메뉴 항목의 수는 {{WebExtAPIRef("menus.ACTION_MENU_TOP_LEVEL_LIMIT")}}지만 서버메뉴에는 얼마든지 추가할 수 있다.
- password
  - : [password 입력 요소](/ko/docs/Web/HTML/Element/input/password)를 콘텍스트-클릭할 때 적용된다.
- selection
  - : 페이지 일부가 선택되었을 때 적용된다.
- tab
  - : 탭을 콘텍스트-클릭할 때 적용된다(specifically, this refers to the tab-strip or other user interface element enabling the user to switch from one browser tab to another, not to the page itself).파이어폭스 63부터, 탭에서 메뉴 항목을 클릭하면 그것이 설사 현재탭이 아니더라도 클릭한 탭에 대해 [activeTab](/ko/docs/Mozilla/Add-ons/WebExtensions/manifest.json/permissions#activeTab_permission) 권한이 승인된다.
- tools_menu
  - : 항목은 브라우저 툴바의 메뉴로 추가된다. 주의해야 할 것은 `menus` 이름공간을 통해 `ContextType`에 접근해야지 `contextMenus` 이름공간으로 하면 안된다.
- video
  - : [video](/ko/docs/Web/HTML/Element/video) 요소에 콘텍스트-클릭을 할 때 적용된다.

"launcher"는 지원되지 않는다.

## 브라우저 호환성

{{Compat("webextensions.api.menus.ContextType", 10)}}

{{WebExtExamples}}

> **참고:** **Acknowledgements**This API is based on Chromium's [`chrome.contextMenus`](https://developer.chrome.com/extensions/contextMenus#type-ContextType) API. This documentation is derived from [`context_menus.json`](https://chromium.googlesource.com/chromium/src/+/master/chrome/common/extensions/api/context_menus.json) in the Chromium code.

```
// Copyright 2015 The Chromium Authors. All rights reserved.
//
// Redistribution and use in source and binary forms, with or without
// modification, are permitted provided that the following conditions are
// met:
//
//    * Redistributions of source code must retain the above copyright
// notice, this list of conditions and the following disclaimer.
//    * Redistributions in binary form must reproduce the above
// copyright notice, this list of conditions and the following disclaimer
// in the documentation and/or other materials provided with the
// distribution.
//    * Neither the name of Google Inc. nor the names of its
// contributors may be used to endorse or promote products derived from
// this software without specific prior written permission.
//
// THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
// "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
// LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
// A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
// OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
// SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
// LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
// DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
// THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
// (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
// OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

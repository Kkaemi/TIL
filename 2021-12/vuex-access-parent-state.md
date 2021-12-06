# Vuex에서 부모 모듈 상태에 접근방법

- parent.js
```javascript
import child from 'some/path';

export default {
  namespaced: true,

  state: {
    parentState: null
  },

  modules: {
    child,
  },
};
```

<br>

- child.js
```javascript
export default {
  namespaced: true,

  actions: {
    async fetchSome({ commit, rootState }) {
      // 부모 상태 가져오기
      const parentState = rootState.parent.parentState;
      
      // ...
    },
  }
}
```

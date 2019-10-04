# vue-max--ts-classes-tests

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Run your end-to-end tests
```
npm run test:e2e
```

### Run your unit tests
```
npm run test:unit
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).




Vue + TS
0) ставим yarn
# ставим глобально yarn:
npm install -g yarn
Сравнение команд → NPM & YARN

 

1) создаем проект:
# ставим глобально vue-cli-3:
npm install -g @vue/cli # или =>  yarn add @vue/cli

# создаем проект:
vue create hello-vue-and-ts
— выбираем manual → выбираем все компоненты (а что мелочиться?!).

— Use class-style component syntax? — Y;

— Use Babel alongside TypeScript for auto-detect polyfills? — Y

— Use history mode for router? — N (или Y)

— Node Dart

— TSlint

— Lint on save

— Pick a unit testing solution — Jest

— Pick a E2E testing solution — Cypress

— Where do you prefer placing config for Babel? — In dedicated config files.

cd hello-vue-and-ts # переход в папку проекта
yarn serve # запуск проекта
2) Ставим необходимые библиотеки
Библиотеки, которые мы будем юзать:

Ставим vue property-decorator, потому, что его все юзают:

yarn add vue-property-decorator --dev
Репо: https://github.com/kaorun343/vue-property-decorator

Он добавляет новый синтаксис:

— позволяет использовать @Component — декоратор, чтобы создать компонент:

@Component({
  template: '<button @click="clickHandler">Кнопочка</button>'
})
— а вместо экспортирования объекта:

export default class MyComponent extends Vue {

  message: string = 'hi!'
  
  clickHandler(): void { window.alert(this.message) }
  
}
Там есть 7 декораторов и 1 функция (mixins):

@Emit, @Inject, @Model, @Prop, @Provide, @Watch, @Component (из vue-class-component), Mixins (из vue-class-component).

Следующий код на vue-class-component:

import {Vue, Class, Prop} from 'vue-class-decorator' 
@Component 
export default class YourComponent extends Vue {
    @Prop(Number) propExample!: number
    @Prop({default: 'default val.'}) propExample2!: string
    @Prop([String, Boolean]}) propExample3: string | boolean
}
Эквивалентен старому:

export default {
  props: {
    propExample: Number,
    propExample2: {default: 'default val.'},
    propExample3: {type: [String, Boolean]},
  }
}
Это помогает чекать типы пропсов компонентов.

Покрытие VUEX типами:
yarn add vuex-module-decorators
Пример кода:

import {Module, VuexModule, Mutation, Action} from 'vuex-module-decorators'
@Module 
export default class Couter extends VuexModule {
  count = 0
    
 @Mutation 
  increment(delta: number) { this.count += delta }
 @Mutation 
  decrement(delta: number) { this.count -= delta }
 
 @Action({commit: 'increment'}) //экшн incr комитит мутацию, когда закончит функцию и выведет 5
  incr() {
   return 5
  }  
}
3) Разбираемся с кодом
src\views\Home.vue

Видим, что импортируется Component и Vue из 'vue-property-decorator'




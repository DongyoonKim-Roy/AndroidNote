# Dependency Injection (DI)
- It is a pattern used to manage the dependencies of classes to promote better code structure and scalability.
- It helps developers create more maintainable, testable, and modular applications.

# Why Dependency Injection?
**Decoupling**
- DI decouples components, like Activities, Fragments, and ViewModels, from the logic of how dependencies are created.

**Testability**
- Injecting dependencies makes it easy to use mock objects for unit testing, leading to more reliable test coverage.

**Reusability and Scalability**
- DI makes code easier to reuse and maintain by promoting a clean architecture.

# Common DI Frameworks
**Dagger**
- Compile-time DI.
- It is powerful but can have a steeper learning curve due to its extensive use of annotations and code generation.

**Hilt**
- Built on top of Dagger, Hilt simplifies DI and integrates well with the Android lifecycle.
- It's easier to set up and use than Dagger.

**Koin**
- A lightweight, Kotlin-based DI framework taht is easy to set up and use, making ti a good alternative to Dagger/Hilt

# Dagger Annotations
## @Module
**Purpose**
- Indicates that a class is a Dagger Module.
- A module is used to provide dependencies that cannot be crated with constructor injection alone.

**Usage**
- Annotate a class to signify that it will contain methods that provide dependencies.

**Example**
```kt
@Module
class NetworkModule {
  @Provides
  fun provideRetrofit(): Retrofit {
    return Retrofit.Builder().baseurl("https://example.com").build()
  }
}
```

## @Provides
**Purpose**
- Specifies that a method within a `@Module` class provides a dependency.

**Usage**
- Use this annotation on methods within a `@Module` to tell Dagger how to construct and provide instances of a dependency.

**Example**
```kt
@Module
class DatabaseModule {
    @Provides
    fun provideDatabase(context: Context): MyDatabase {
        return MyDatabase.create(context)
    }
}
```

## @Component
**Purpose**
- Marks an interface as a Dagger component.
- A component is a bridge between `@Module` classes and where dependencies are injected.

**Usage**
- Annotate an interface to define which modules and dependencies are available for injection.

**Example**
```kt
@Component(modules = [NetworkModule::class, DatabaseModule::class])
interface AppComponent {
    fun inject(activity: MainActivity)
}
```

## @Inject
**Purpose**
- Requests dependency injection.
- It tells Dagger where to inject the dependencies.

**Usage**
- Annotate a constructor, field or method to request an injected dependency.

**Example**
```kt
class UserRepository @Inject constructor(private val apiService: ApiService) {
    // Dagger will provide an instance of ApiService when creating UserRepository
}
```

## @Singleton
**Purpose**
- Marks a provided dependency as a singleton, meaning only one instance of the dependency will be created and shared.

**Usage**
- Use this annotation on a `@Provides` method or `@Component` interface to specify a singleton-scoped dependency.

**Example**
```kt
@Module
class AppModule {
    @Provides
    @Singleton
    fun provideApiService(): ApiService {
        return ApiService.create()
    }
}
```

## @Scope
**Purpose**
- Used to create custom scopes for dependencies.
- This helps manage the lifecycle of a dependency in a more granular way than `@Singleton`.

**Usage**
- Created and use custom annotations to define your own scoped dependencies.

**Example**
```kt
@Scope
@Retention(AnnotationRetention.RUNTIME)
annotation class ActivityScope
```

## @Qualifier
**Purpose**
- Used to differentiate between different implementations of the same type.
- It helps avoid ambiguity when there are multiple bindings of the same type.

**Usage**
- Created custom qualifiers using this annotation and appy them to `@Provides` methods or `@Inject` fields.

**Example**
```kt
@Qualifier
@Retention(AnnotationRetention.RUNTIME)
annotation class Authenticated

@Module
class NetworkModule {
    @Provides
    @Authenticated
    fun provideAuthenticatedApiService(): ApiService {
        return ApiService.createAuthenticated()
    }

    @Provides
    fun provideApiService(): ApiService {
        return ApiService.create()
    }
}
```

## @Binds
**Purpose**
- Used in modules to tell Dagger which implementation to use when an interface is requested.

**Usage**
- Unlike `@Provides`, `@Binds` methods must be abstract and are often more efficient.

**Example**
```kt
@Module
interface RepositoryModule {
    @Binds
    fun bindUserRepository(impl: UserRepositoryImpl): UserRepository
}
```

## @Subcomponent
**Purpose**
- Defines a subcomponent that can inherit dependencies from its parent component.
- This helps manage dependencies with different lifecycles.

**Usage**
- Annotate an interface to define a subcomponent.

**Example**
```kt
@Subcomponent
interface ActivityComponent {
    fun inject(activity: MainActivity)
}
```

# Example
`build.gradle.kts`

```kt
plugins {
    alias(libs.plugins.android.application)
    alias(libs.plugins.kotlin.android)
    id ("kotlin-kapt") //added
}
.
.
.
dependencies {
    implementation(libs.androidx.core.ktx)
    implementation(libs.androidx.appcompat)
    implementation(libs.material)
    implementation(libs.androidx.activity)
    implementation(libs.androidx.constraintlayout)
    testImplementation(libs.junit)
    androidTestImplementation(libs.androidx.junit)
    androidTestImplementation(libs.androidx.espresso.core)
    implementation ("com.google.dagger:dagger:2.48.1") //added
    kapt ("com.google.dagger:dagger-compiler:2.48.1") //added
}
```

`ClassA.kt`
```kt
class ClassA @Inject constructor() {
  fun startClassA() {
    Log.i("TAG", "Class A")
  }
}
```

`ClassB.kt`
```kt
class ClassB @Inject constructor() {
  fun startClassB() {
    Log.i("TAG", "Class B")
  }
}
```

`ClassC.kt`
```kt
class ClassC @Inject constructor(val classA: ClassA, val classB: ClassB) {
  fun startClassC() {
    classA.startClassA()
    classB.startClassB()
    Log.i("TAG", "Class C")
  }
}
```

`ClassABModule`
```kt@Module
object ClassABModule {

    @Provides
    fun provideClassA(): ClassA{
        return ClassA()
    }

    @Provides
    fun provideClassB(): ClassB{
        return ClassB()
    }
}
```

`ClassCComponent`
```kt
@Component(modules = [ClassABModule::class])
interface ClassCComponent {
    fun getClassCInstance(): ClassC
}
```

`MainActivity.kt`
```kt
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        DaggerClassCComponent.create().getClassCInstance().startClassC()
    }
}
```

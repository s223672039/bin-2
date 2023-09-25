<template>
    <div>
        <!-- Template Syntax -->
        <p>{{ message }}</p>
        <div v-html="rawHTML"></div>
        <input :id="inputId" />
        <p>{{ uppercaseMessage() }}</p>

        <!-- Methods -->
        <button @click="changeMessage">Change Message</button>

        <!-- Reactivity Fundamentals -->
        <p>{{ count }}</p>
        <button @click="incrementCount">Increment Count</button>

        <!-- Computed Properties -->
        <div>
            <p>Computed Property: {{ computedProperty }}</p>
            <input type="text" v-model="inputValue" />
            <button @click="updateInputValue">Update Input</button>
        </div>

        <!-- Class and Style Bindings -->
        <div :class="{ 'active': isActive, 'error': hasError }">Class Binding Example</div>
        <div :style="{ 'color': textColor, 'font-size': fontSize + 'px' }">Style Binding Example</div>

        <!-- Event Handling -->
        <div>
            <button @click="handleClickInline">Click Me (Inline)</button>
            <button @click="handleClickMethod">Click Me (Method)</button>
        </div>

        <!-- Form Input Bindings -->
        <div>
            <input type="text" v-model="textValue" />
            <p>Text Value: {{ textValue }}</p>

            <input type="text" v-model.trim="trimmedTextValue" />
            <p>Trimmed Text Value: {{ trimmedTextValue }}</p>

            <input type="checkbox" v-model="checkboxValue" />
            <p>Checkbox Value: {{ checkboxValue }}</p>

            <input type="checkbox" v-model="lazyCheckboxValue" />
            <p>Lazy Checkbox Value: {{ lazyCheckboxValue }}</p>

            <input type="radio" value="option1" v-model="radioValue" />
            <input type="radio" value="option2" v-model="radioValue" />
            <p>Radio Value: {{ radioValue }}</p>

            <select v-model="selectedOption">
                <option value="option1">Option 1</option>
                <option value="option2">Option 2</option>
            </select>
            <p>Selected Option: {{ selectedOption }}</p>

            <input type="number" v-model.number="numericValue" />
            <p>Numeric Value: {{ numericValue }}</p>

            <textarea v-model.trim="trimmedTextareaValue"></textarea>
            <p>Trimmed Textarea Value:</p>
            <pre>{{ trimmedTextareaValue }}</pre>
        </div>

        <!-- List Rendering -->
        <div>
            <!-- a. v-for with an Object -->
            <ul>
                <li v-for="(value, key) in myObject" :key="key">
                    {{ key }}: {{ value }}
                </li>
            </ul>

            <!-- b. v-for with a Range -->
            <ul>
                <li v-for="n in 5" :key="n">{{ n }}</li>
            </ul>

            <!-- c. v-for on <template> -->
            <ul>
                <template v-for="item in items" :key="item.id">
                    <li>{{ item.name }}</li>
                </template>
            </ul>

            <!-- d. v-for with v-if -->
            <ul>
                <li v-for="item in filteredItems" :key="item.id">
                    {{ item.name }}
                </li>
            </ul>

            <!-- e. v-for with a Component -->
            <ul>
                <li v-for="item in itemsWithComponents" :key="item.id">
                    <child-component :message="item.name"></child-component>
                </li>
            </ul>
        </div>

        <!-- Include the ChildComponent -->
        <div>
            <child-component :message="messageFromParent"></child-component>
        </div>
    </div>
</template>

<script>
import { ref, computed } from 'vue';
import ChildComponent from './ChildComponent.vue'; // Import your child component here

export default {
    components: {
        ChildComponent,
    },
    setup() {
        // Template Syntax
        const message = ref('SIT120 Task 2.3C');
        const rawHTML = '<span style="color: cyan;">Raw HTML</span>';
        const inputId = 'my-input';

        // Reactivity Fundamentals
        const count = ref(0);

        // Computed Properties
        const inputValue = ref('Hello, Vue!');
        const computedProperty = computed(() => inputValue.value.toUpperCase());

        // Class and Style Bindings
        const isActive = ref(true);
        const hasError = ref(false);
        const textColor = ref('blue');
        const fontSize = ref(16);

        // Form Input Bindings
        const textValue = ref('');
        const trimmedTextValue = ref('');
        const checkboxValue = ref(false);
        const lazyCheckboxValue = ref(false);
        const radioValue = ref('');
        const selectedOption = ref('option1');
        const numericValue = ref(0);
        const trimmedTextareaValue = ref('');

        // Methods
        const uppercaseMessage = () => {
            return message.value.toUpperCase();
        };

        const changeMessage = () => {
            message.value = 'No chance of plagiarism';
        };

        const incrementCount = () => {
            count.value++;
        };

        const updateInputValue = () => {
            inputValue.value = 'Updated Value';
        };

        // Event Handlers
        const handleClickInline = () => {
            alert('Inline click handler');
        };

        const handleClickMethod = () => {
            alert('Method click handler');
        };

        // Components
        const messageFromParent = 'Hello from Parent!';

        // Sample data for list rendering examples
        const myObject = { key1: 'value1', key2: 'value2' };
        const items = [
            { id: 1, name: 'Item 1' },
            { id: 2, name: 'Item 2' },
        ];
        const itemsWithComponents = [
            { id: 1, name: 'Item 1' },
            { id: 2, name: 'Item 2' },
        ];

        // Computed property for filteredItems
        const filteredItems = computed(() => {
            return items.filter(item => item.condition); // Make sure condition property exists
        });

        return {
            message,
            rawHTML,
            inputId,
            count,
            inputValue,
            computedProperty,
            isActive,
            hasError,
            textColor,
            fontSize,
            textValue,
            trimmedTextValue,
            checkboxValue,
            lazyCheckboxValue,
            radioValue,
            selectedOption,
            numericValue,
            trimmedTextareaValue,
            uppercaseMessage,
            changeMessage,
            incrementCount,
            updateInputValue,
            handleClickInline,
            handleClickMethod,
            messageFromParent,
            myObject,
            items,
            itemsWithComponents,
            filteredItems,
        };
    },
};
</script>

python_lib(cairo_compile_lib
    PREFIX starkware/cairo/lang/compiler
    FILES
    __init__.py
    assembler.py
    ast/__init__.py
    ast/arguments.py
    ast/bool_expr.py
    ast/cairo_types.py
    ast/code_elements.py
    ast/expr.py
    ast/formatting_utils.py
    ast/imports.py
    ast/instructions.py
    ast/module.py
    ast/node.py
    ast/notes.py
    ast/rvalue.py
    ast/types.py
    ast/visitor.py
    cairo_compile.py
    cairo_format.py
    cairo.ebnf
    constants.py
    const_expr_checker.py
    debug_info.py
    encode.py
    error_handling.py
    expression_evaluator.py
    expression_simplifier.py
    expression_transformer.py
    fields.py
    identifier_definition.py
    identifier_manager.py
    identifier_manager_field.py
    identifier_utils.py
    import_loader.py
    instruction_builder.py
    instruction.py
    location_utils.py
    module_reader.py
    parser_transformer.py
    parser.py
    preprocessor/compound_expressions.py
    preprocessor/flow.py
    preprocessor/identifier_collector.py
    preprocessor/local_variables.py
    preprocessor/preprocessor_error.py
    preprocessor/preprocessor_utils.py
    preprocessor/preprocessor.py
    preprocessor/reg_tracking.py
    program.py
    references.py
    scoped_name.py
    substitute_identifiers.py
    type_system_visitor.py

    LIBS
    cairo_version_lib
    starkware_expression_string_lib
    starkware_python_utils_lib
    pip_marshmallow_dataclass
    pip_marshmallow_enum
    pip_marshmallow_oneofschema
    pip_marshmallow
    pip_lark_parser
)

python_exe(cairo_compile_exe
    VENV cairo_lang_venv
    MODULE starkware.cairo.lang.compiler.cairo_compile
)

python_venv(cairo_format_venv
    PYTHON python3.7
    LIBS
    cairo_compile_lib
)

python_exe(cairo_format
    VENV cairo_format_venv
    MODULE starkware.cairo.lang.compiler.cairo_format
)

python_lib(cairo_compile_test_utils_lib
    PREFIX starkware/cairo/lang/compiler
    FILES
    preprocessor/preprocessor_test_utils.py
    test_utils.py

    LIBS
    cairo_compile_lib
    pip_pytest
)

full_python_test(cairo_compile_test
    PREFIX starkware/cairo/lang/compiler
    PYTHON python3.7
    TESTED_MODULES starkware/cairo/lang/compiler

    FILES
    assembler_test.py
    ast_objects_test.py
    ast/formatting_utils_test.py
    cairo_compile_test.py
    encode_test.py
    error_handling_test.py
    expression_evaluator_test.py
    expression_simplifier_test.py
    identifier_definition_test.py
    identifier_manager_field_test.py
    identifier_manager_test.py
    identifier_utils_test.py
    import_loader_test.py
    instruction_builder_test.py
    instruction_test.py
    module_reader_test.py
    parser_errors_test.py
    parser_test.py
    preprocessor/compound_expressions_test.py
    preprocessor/flow_test.py
    preprocessor/identifier_collector_test.py
    preprocessor/local_variables_test.py
    preprocessor/preprocessor_test.py
    preprocessor/reg_tracking_test.py
    references_test.py
    scoped_name_test.py
    type_system_visitor_test.py

    LIBS
    cairo_compile_lib
    cairo_compile_test_utils_lib
    pip_pytest
)

add_definitions(-DCPPHTTPLIB_OPENSSL_SUPPORT)

foreach (_target
		benchmark client hello redirect server simplecli simplesvr ssecli ssesvr upload
		)
	add_executable(cpp-httplib-${_target} ${_target}.cc)
	target_include_directories(cpp-httplib-${_target} PUBLIC ../ ${OPENSSL_INCLUDE_DIR})
	target_link_libraries(cpp-httplib-${_target} OpenSSL::Crypto OpenSSL::SSL)
endforeach ()